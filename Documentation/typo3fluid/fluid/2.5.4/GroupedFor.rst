.. include:: ../../../Includes.txt

==========
groupedFor
==========


Grouped loop view helper.
Loops through the specified values.

The groupBy argument also supports property paths.

= Examples =

<code title="Simple">
<f:groupedFor each="{0: {name: 'apple', color: 'green'}, 1: {name: 'cherry', color: 'red'}, 2: {name: 'banana', color: 'yellow'}, 3: {name: 'strawberry', color: 'red'}}" as="fruitsOfThisColor" groupBy="color">
  <f:for each="{fruitsOfThisColor}" as="fruit">
    {fruit.name}
  </f:for>
</f:groupedFor>
</code>
<output>
apple cherry strawberry banana
</output>

<code title="Two dimensional list">
<ul>
  <f:groupedFor each="{0: {name: 'apple', color: 'green'}, 1: {name: 'cherry', color: 'red'}, 2: {name: 'banana', color: 'yellow'}, 3: {name: 'strawberry', color: 'red'}}" as="fruitsOfThisColor" groupBy="color" groupKey="color">
    <li>
      {color} fruits:
      <ul>
        <f:for each="{fruitsOfThisColor}" as="fruit" key="label">
          <li>{label}: {fruit.name}</li>
        </f:for>
      </ul>
    </li>
  </f:groupedFor>
</ul>
</code>
<output>
<ul>
  <li>green fruits
    <ul>
      <li>0: apple</li>
    </ul>
  </li>
  <li>red fruits
    <ul>
      <li>1: cherry</li>
    </ul>
    <ul>
      <li>3: strawberry</li>
    </ul>
  </li>
  <li>yellow fruits
    <ul>
      <li>2: banana</li>
    </ul>
  </li>
</ul>
</output>

Note: Using this view helper can be a sign of weak architecture. If you end up using it extensively
you might want to fine-tune your "view model" (the data you assign to the view).

Arguments
=========


each (anySimpleType)
--------------------


The array or \SplObjectStorage to iterated over

as (string)
-----------


The name of the iteration variable

groupBy (string)
----------------


Group by this property

groupKey (string)
-----------------


Default: &#039;groupKey&#039;

The name of the variable to store the current group