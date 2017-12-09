---
id: 813
disqus_id: 813 http://regis.decamps.info/blog/?p=813
title: Managed extensibility framework
date: 2009-02-11T12:26:18+00:00
author: Régis
layout: post
guid: http://regis.decamps.info/blog/?p=813
permalink: /blog/2009/02/managed-extensibility-framework/
dsq_thread_id:
  - "189257713"

categories:
  - English
  - Programmation
tags:
  - Dotnet
  - Microsoft
---
I went yesterday to the MS Techdays and the most interesting talk I listen to was about MEF.
  
[
  
Introduced last year](http://blogs.msdn.com/kcwalina/archive/2008/04/25/MEF.aspx), [MEF](http://www.codeplex.com/MEF) is a « Managed extensibility framework » by Microsoft. It is a framework that helps to develop pluggable components in MS .net.

Similarly to the [IoC design pattern](http://en.wikipedia.org/wiki/Inversion_of_control), a given behaviour is not implemented directly in the core of the program. Instead, it relies on an interface, and the implementation is provided by another module. Martin Fowler wrote several years ago a very good article to [introduce Inversion of control and dependency injection](http://martinfowler.com/articles/injection.html).

In Java such frameworks have been around for a while, have a look on [Spring](http://www.springFramework.org/) or [Google Juice](http://code.google.com/p/google-guice/) for instance.
  
<!--more-->


  
In the MEF Shape example, the interface for a shape is a IShape.

The game imports shapes (in other words, a shape is an extension point)
  
[csharp]
      
public class MefShapesGame:IMefShapesGame
      
{
          
…;
          
[Import]
          
public ObservableCollection<Export<IShape, IShapeMetadata>> SelectionShapes { get; private set; }
          
…;
      
}
  
[/csharp]

Of course, the game has many shapes. For instance, one of them is a diagonal:
  
[csharp]
      
[Export(typeof(IShape))]
      
[Shape(ShapeType.GameShape, « Diagonal shape », 0)]
      
[CompositionOptions(CreationPolicy = CreationPolicy.Factory)]
      
public class Diagonal : RegularShape
      
{
          
…;
      
}
  
[/csharp]

The extension point and a possible implementation are put together thanks to the Compose() method of the main program. This composition is made « magically », simply by providing the the assembly of that requires a shape (the game), and the assembly that provides many shapes.
  
[csharp]
      
private bool Compose()
      
{
          
var catalog = new AggregatingComposablePartCatalog();
          
catalog.Catalogs.Add(new AttributedAssemblyPartCatalog(typeof(IMefShapesGame).Assembly));
          
catalog.Catalogs.Add(new AttributedAssemblyPartCatalog(typeof(DefaultDimensions).Assembly));
          
_container = new CompositionContainer(catalog);
          
_container.AddPart(this);
          
_container.AddExportedObject<ICompositionService>(_container);
          
_container.AddExportedObject<AggregatingComposablePartCatalog>(catalog);
          
try
          
{
              
_container.Compose();
          
}
          
catch (CompositionException compositionException)
          
{
              
MessageBox.Show(compositionException.ToString());
              
return false;
          
}
          
return true;
      
}
  
[/csharp]

MEF is there for developping plugins in dotnet. The extension point can have different behaviour in case several implementations are found: raise an exception ; use the first one only ; build a collection of all of them.

Now, what makes MEF better from previously existing frameworks for depency injection, like Castle, Spring.net or Ninject?
