# Merge-Table-with-Dynamic-Rows-ZohoWriter
A Deluge script that dynamically builds a HTML table with alternating row colors and merges into a Zoho Writer template.

## Core Idea
Suppose you have a subform called Items in Deals. On a click of a button, you want to generate a PDF document via Zoho Writer with the subform rows merged into a table. If the number of rows in the table is fixed, you can create the table on the Writer template, set plain text merge fields as the table values, and merge it with Deluge. However, if the number of rows in the table varies, you need to dynamically create the table in Deluge, then merge the entire table into the Writer template via a Rich Text Field.

## Tutorial 

## Create a Rich Text Merge Field on Your Writer Template
On the side toolbar, go to Fields --> Merge Fields (Under Dynamic Fields) --> Click on the Setting Cogwheel next to Field List --> Add a New Field (Rich Text)
* In this example, the rich text field label is "table".

## Write Your Deluge Function

### Get the Subform
Change "Items" to your respective subform name.
* This is just an example. For your application, it could be a subform, related list, or any other types of list.

```javascript
deal = zoho.crm.getRecordsbyId("Deals",dealid);
items = deal.get("Items");
```

### Build the Table
The meat of the script starts here. Once you have your list (in this example, Items subform), do the following:

#### Set the Headers for the Table & Define the Counters
* headers: Start building your table here by creating the headers and customizing the table properties (cellpading/cellspacing/width/background color/etc).
  * In this table example, the headers are Name, Serial Number and Quantity.
* bodytext: Set to an empty string. This will be used to build the rows of the table.
* n: Set it as 0. This will be used later to alternate the table row colors.

```javascript
headers = "<table cellpadding=8 cellspacing=4 style=width:100%><tr bgcolor=#F3F6F9><td><b><font color=000000>Name</font></b></td><td><b><font color=000000>SKU</font></b></td><td><b><font color=000000>Serial Number</font></b></td><td><b><font color=000000>Quantity</font></b></td></tr>";
bodytext = "";
n = 0;
```

#### Iterate through the List, Build the Table Contents, 
