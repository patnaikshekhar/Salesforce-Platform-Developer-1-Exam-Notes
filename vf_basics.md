# Visualforce Basics

* In order to use a Standard List controller, add the **recordSetVar** attribute to the ```<apex:page>``` tag
* The ```<apex:pageBlock/>``` and ```<apex:pageBlockSection />``` tags create some user interface elements which match the standard UI style
* The pageBlockSection tag has a **columns** element which lets you set the number of columns in the section.
* The ```<apex:pageBlockTable value="{!products}" var="pitem">``` tag adds the standard visualforce table.
* The **column** tag creates a column in the table
```html
<apex:pageBlockTable value="{!products}" var="pitem">
    <apex:column headerValue="Product">
        <apex:outputText value="{!pitem.Name}"/>
    </apex:column>
</apex:pageBlockTable>
```
* The **tabStyle** attribute of ```apex:page``` will make sure that the tab is displayed as the Object Name when a standardController is not used
* The **$User** variable is used to access user details
* The ```<apex:detail />``` tag is used to display the standard view page for a record
* The relatedList tag is used to display related lists
```html
<apex:relatedList list="Cases" />
```
* **rerender** attribute is used on certain tags to re-render a section
* Ways to display visualforce
  * Override Standard Pages
  * Embed a page in a standard layout
  * Create a button that links to a VF page
  * VF Pages can be used in public facing sites
* **$Page.pageName** is used to get a link reference to another page
* You can link to default actions in your pages.
```html
<apex:outputLink value="{!URLFOR($Action.Account.new)}">Create</apex:outputLink>
```
* ```<apex:pageMessages />``` is used to show errors
* ```<apex:inputField />``` and ```<apex:outputField />``` also show the field labels
* Templates
  * Use ```<apex:insert>``` to insert a placeholder in a template
  e.g.
    ```html
    <apex:page>
      <h1>My Fancy Site</h1>
      <apex:insert name="body"/>
  </apex:page>
    ```
    * Use the template by using the ```<apex:define />``` tag
    ```html
    <apex:page sidebar="false" showHeader="false">
    <apex:composition template="BasicTemplate">
        <apex:define name="body">
            <p>This is a simple page demonstrating that this
               text is substituted, and that a banner is created.</p>
        </apex:define>
   </apex:composition>
   </apex:page>
   ```
   * Another way to include a page is to use the ```<apex:include />``` tag
   ```html
   <apex:page sidebar="false" showHeader="false"> <p>Test Before</p>
      <apex:include pageName="MainPage"/> <p>Test After</p>
   </apex:page>
   ```
* Use the **$Resource** variable to access static resources
* Use ```Visualforce.remoting.Manager.invokeAction('{!$RemoteAction.ClassName.MethodName}')``` to invoke a remote action
* Use the following to format an output text in currency format
```html
<apex:outputText value="{0,number,currency}">
    <apex:param value="{!pitem.Price}"/>
</apex:outputText>
```