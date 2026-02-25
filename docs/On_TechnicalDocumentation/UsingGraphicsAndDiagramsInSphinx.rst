:tocdepth: 2

.. highlight:: none

.. metadata-placeholder

   :DC.Title:
   	Creating diagrams
   :DC.Creator:
   	Nery, Fernanda
   :DC.Date:
   	2013-10-01
   :DC.Description:
      Overview of some available alternatives for
      producing and including SVG graphics and UML diagrams in Sphinx.
   :DC.Language:
   	en
   :DC.Format:
   	text/x-rst

.. _rst-diagrams-ref:

Creating diagrams
***************************

.. contents:: On this page...
   :depth: 3
   :local:

.. warning:: 
   
   This page is a work in progress. 
   Examples will be added soon.

Using Mermaid
==============

This extension allows you to embed Mermaid_ graphs in your documents, including general flowcharts, sequence diagrams, gantt diagrams and more.

It adds a directive to embed mermaid markup. 

Sequence diagrams
------------------
 
This sequence diagram...

.. _block_begin_202602251651:

.. mermaid::

   sequenceDiagram
      participant Alice
      participant Bob
      participant Charlie
      Alice->Bob: How are you?
      loop Thinking
          Bob->Bob: I need a holiday...
      end
      Note right of Bob: Just reply <br/>something...
      Bob-->Alice: Great!
      Bob->Charlie: How about you?
      Charlie-->Bob: Jolly good!

.. _block_end_202602251651:

...is created by this block of code:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :start-after: block_begin_202602251651
   :end-before: block_end_202602251651

Class diagrams
------------------

This class diagram...

.. _block_begin_202602251652:

.. mermaid::

   classDiagram
    %% Relationships
    Animal <|-- Duck
    Animal <|-- Fish
    Animal <|-- Zebra

    %% Class Definitions
    class Animal {
        +String name
        +int age
        +isMammal() bool
        +mate()
    }

    class Duck {
        +String beakColor
        +swim()
        +quack()
    }

    class Fish {
        -int sizeInFeet
        -canEat()
    }

    class Zebra {
        +bool is_wild
        +run()
    }

.. _block_end_202602251652:

...is created by this block of code:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :start-after: block_begin_202602251652
   :end-before: block_end_202602251652

Using Graphviz
==============

Besides using raster images (PNG, JPG, etc.),
diagrams can be included with
the `sphinx.ext.graphviz`_ extension.

Graphviz_ is an open source graph visualisation software.
Graph visualisation is a way of representing structural information
as diagrams of abstract graphs and networks.

The Graphviz extension is included with Sphinx,
but must be enabled in the ``conf.py`` file::

   extensions = ['sphinx.ext.graphviz']
   

Simple graph example
--------------------

This simple graph...

.. _block_begin_202602251653:

.. graphviz::

   digraph {
      "From" -> "To";
   }

.. _block_end_202602251653:

...is created by this block of code:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :start-after: block_begin_202602251653
   :end-before: block_end_202602251653

Graph with colourful shapes example
-----------------------------------
  
This graph with different shapes and styles for each node:

.. _block_begin_202602251654:

.. graphviz::

   digraph Flatland {
   
      a -> b -> c -> g; 
      a  [shape=polygon,sides=4]
      b  [shape=polygon,sides=5]
      c  [shape=polygon,sides=6]
   
      g [peripheries=3,color=yellow];
      s [shape=invtriangle,peripheries=1,color=red,style=filled];
      w [shape=triangle,peripheries=1,color=blue,style=filled];
      
      }

.. _block_end_202602251654:

...is created by this block of code:

.. literalinclude:: UsingGraphicsAndDiagramsInSphinx.rst
   :start-after: block_begin_202602251654
   :end-before: block_end_202602251654

More examples are available online:

*  https://en.wikipedia.org/wiki/DOT_(graph_description_language)
*  http://www.graphviz.org/pdf/dotguide.pdf
*  http://graphs.grevian.org


.. links-placeholder

.. include:: ../_sharedFiles/Links.rst