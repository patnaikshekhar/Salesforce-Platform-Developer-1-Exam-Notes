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