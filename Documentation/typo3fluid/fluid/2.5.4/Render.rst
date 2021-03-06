.. include:: ../../../Includes.txt

======
render
======


A ViewHelper to render a section, a partial, a specified section in a partial
or a delegate ParsedTemplateInterface implementation.

= Examples =

<code title="Rendering partials">
<f:render partial="SomePartial" arguments="{foo: someVariable}" />
</code>
<output>
the content of the partial "SomePartial". The content of the variable {someVariable} will be available in the partial as {foo}
</output>

<code title="Rendering sections">
<f:section name="someSection">This is a section. {foo}</f:section>
<f:render section="someSection" arguments="{foo: someVariable}" />
</code>
<output>
the content of the section "someSection". The content of the variable {someVariable} will be available in the partial as {foo}
</output>

<code title="Rendering recursive sections">
<f:section name="mySection">
 <ul>
   <f:for each="{myMenu}" as="menuItem">
     <li>
       {menuItem.text}
       <f:if condition="{menuItem.subItems}">
         <f:render section="mySection" arguments="{myMenu: menuItem.subItems}" />
       </f:if>
     </li>
   </f:for>
 </ul>
</f:section>
<f:render section="mySection" arguments="{myMenu: menu}" />
</code>
<output>
<ul>
  <li>menu1
    <ul>
      <li>menu1a</li>
      <li>menu1b</li>
    </ul>
  </li>
[...]
(depending on the value of {menu})
</output>


<code title="Passing all variables to a partial">
<f:render partial="somePartial" arguments="{_all}" />
</code>
<output>
the content of the partial "somePartial".
Using the reserved keyword "_all", all available variables will be passed along to the partial
</output>


<code title="Rendering via a delegate ParsedTemplateInterface implementation w/ custom arguments">
<f:render delegate="My\Special\ParsedTemplateImplementation" arguments="{_all}" />
</code>
<output>
Whichever output was generated by calling My\Special\ParsedTemplateImplementation->render()
with cloned RenderingContextInterface $renderingContext as only argument and content of arguments
assigned in VariableProvider of cloned context. Supports all other input arguments including
recursive rendering, contentAs argument, default value etc.
Note that while ParsedTemplateInterface supports returning a Layout name, this Layout will not
be respected when rendering using this method. Only the `render()` method will be called!
</output>

Arguments
=========


section (string)
----------------


Section to render - combine with partial to render section in partial

partial (string)
----------------


Partial to render, with or without section

delegate (string)
-----------------


Optional PHP class name of a permanent, included-in-app ParsedTemplateInterface implementation to override partial/section

renderable (anySimpleType)
--------------------------


Instance of a RenderableInterface implementation to be rendered

arguments (anySimpleType)
-------------------------


Default: array ()

Array of variables to be transferred. Use {_all} for all variables

optional (boolean)
------------------


Default: false

If TRUE, considers the *section* optional. Partial never is.

default (anySimpleType)
-----------------------


Value (usually string) to be displayed if the section or partial does not exist

contentAs (string)
------------------


If used, renders the child content and adds it as a template variable with this name for use in the partial/section