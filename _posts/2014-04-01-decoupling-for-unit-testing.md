---
title: Decoupling Code to Facilitate Unit Testing 
layout: post
comments: True
draft: True
---

THIS IS A DRAFT POST FOR COMMENTARY!

Something that I've run into many times when working on existing apps is the ammount (or lack thereof) of decoupling shown. Historically it's been a bit of a pain to properly decouple your code and still keep it managable, but the variety of dependency injection frameworks that exist now leaves almost no excuse. Since I've been using AutoFac more than anything in my latest project, I'll be writing this with the AutoFac calls in mind, but the same features are available in most of the containers available.

Let's take the following (completely legitimate and real world ready) example:

{% highlight csharp %}

public class ClassWithSingleDependency
{
	IWorker _worker;
	
	public ClassWithSingleDependency()
	{
		_worker = new Worker();
	}
	
	public string DoSomeWork(string input)
	{
		return worker.DoTheThing(input);
	}
}

{% endhighlight %}

So despite being a pointless abstraction, there's something seriously wrong with the above code, particularly when it comes to testing. Let's make a new class that has two dependencies and lets see how we might go about testing it:

{% highlight csharp %}
	
public class ClassWithMultipleDependencies
{
	IWorker _thisWayWorker;
	IWorker _thatWayWorker;
	
	public ClassWithMultipleDependencies()
	{
		_thisWayWorker = new ThisWayWorker();
		_thatWayWorker = new ThatWayWorker();	
	}
	
	public string DoSomeConditionalWork(string condition, string input)
	{
		if(condition == "DO IT THIS WAY")
		{				
			return _thisWayWorker.DoTheThing(input);
		}
		else
		{
			return _thatWayWorker.DoTheThing(input);
		}
	}
}

{% endhighlight %}

So now we're starting to do something more interesting, we've got a condition in here and we're dependant on two external concrete types. This is a testability nightmare. I want to be able to test the conditional code and make sure the correct decision is being made around which worker is being resolved. In order to excercise the decision making in the if statement, the test will instantiate a new instance of ClassWithMultipleDependencies, this will execute the constructor and instantiate a ThisWayWorker and a ThatWayWorker. Suddenly our test is no longer excercising just the condition and is now extremely fragile, if someone breaks the "ThisWayWorker" constructor then any test that works on the class above will fail too despite there being nothing wrong with that code, it makes finding the root cause of a test failure a hell of a lot harder. It might not be a big deal when you've got 50 tests, but when you've got 1,000 or how about 10,000 tests? What then? You end up spending half your day figuring out what the common part of all of the failing tests is, instead of just getting down to fixing the broken code.

So how should it look? Let's see the first one:

{% highlight csharp %}

public class ClassWithSingleDependency
{		
	IWorker _worker;
	
	public ClassWithSingleDependency(IWorker worker)
	{
		//initialise some variables, do some spin up work, etc.
		_worker = worker;
	}
	
	public string DoSomeWork(string input)
	{
		return _worker.DoTheThing(input);
	}
}
	
{% endhighlight %}

So we've made one significant change, instead of the constructor instantiating the worker, we've now advertised that we have a dependency in our constructor and stated that we cannot instantiate this type without fulfilling that dependency. This is a perfectly valid practice even without a DI container, but utilising something like AutoFac, Ninject or Unity makes resolving these dependencies childs play however I'm going to do another blog post on the various ways DI containers get abused, why they are bad, and how we should be utilising them instead. The implication of this is that our unit tests can now inject a mocked version of an IWorker which is fully under the test methods control and all of the code that is being excercised is either in the test method itself or in the specific class under test. This is now "unit-testable", previously the code was still somewhat testable, it is just not *unit*testable, if your test excercises more than one unit of code, it is no longer a unit test.

So that was an easy example, let's have a look at how we go about de-coupling the second example:

{% highlight csharp %}

public class ClassWithMultipleDependencies
{
	IWorkerFactory _workerFactory;		
	
	public ClassWithMultipleDependencies(IWorkerFactory workerFactory)
	{
		_workerFactory = workerFactory;	
	}
	
	public string DoSomeConditionalWork(string condition, string input)
	{
		var worker = _workerFactory.Do(condition);
		return worker.DoTheThing(input);			
	}
}

{% endhighlight %}

This is a much more significant change, and now the above example is no longer complete, we're going to need the following also:

{% highlight csharp %}

public class WorkerFactory : IWorkerFactory
{
	public IWorker Do(string condition)
	{
		if(condition == "DO IT THIS WAY")
		{
			return new ThisWayWorker();
		}
		return new ThatWayWorker();
	}
}

{% endhighlight %}

This is better, we can definitely unit test the original class now by providing a mock factory, but we've moved the conditional logic else-where and now that too needs testing! This is where a DI container really starts to shine. With a DI container we get rid of the factory implementation and instead our class starts to look like this:

{% highlight csharp %}

public class ClassWithMultipleDependencies
{
	Func<string, IWorker> _workerFactory;		
	
	public ClassWithMultipleDependencies(Func<string, IWorker> workerFactory)
	{
		_workerFactory = workerFactory;	
	}
	
	public string DoSomeConditionalWork(string condition, string input)
	{
		var worker = _workerFactory(condition);			
		return worker.DoTheThing(input);			
	}
}
	
{% endhighlight %}

And we define our factory function to be loaded into the DI container so it looks something like this:

{% highlight csharp %}

public class MappingModule
{

	public void LiveMappings()
	{
		container.Register<IWorker>().As<ThisWayWorker>("thisWayWorker");
		container.Register<IWorker>().As<ThatWayWorker>("thatWayWorker");
	}		

	public void DependencyContainerBootstrap()
	{
		var factoryFunc = new Func<string, IWorker>( condition => {
			if(condition == "DO IT THIS WAY")
			{	
				return container.Resolve<IWorker>("thisWayWorker");
			}
			return container.Resolve<IWorker>("thatWayWorker");		
		}); 
		container.RegisterInstance(factoryFunc);
	}
}
	
{% endhighlight %}

So now our factory is the responsibility of the DI framework, but the logic is inherently testable thanks to the notion of named instances. For our production code we'll be calling the LiveMappings as part of our bootstrap process, but for our unit tests we are again free to register two different mocks for the IWorkers and name them appropriately. Now we've got full control of our dependencies, and every bit of logic is fully testable!

There's still a hell of a lot more to talk about on this subject, and I'm certainly not the only blogger writing about this stuff, but since I see examples of this being done wrong pretty much everywhere I work I feel compelled to write at least a little bit about it! I've got another blog in the pipeline related to appropriately wrapping external dependencies so we can keep testing even in the face of framework and requirement adversity! 
  
Thanks for reading!
  
Mike

{% include twitter_plug.html %}