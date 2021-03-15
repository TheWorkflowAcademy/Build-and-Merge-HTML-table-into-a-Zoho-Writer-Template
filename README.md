# Merge-Table-with-Dynamic-Rows-ZohoWriter
A Deluge script that dynamically builds a HTML table with alternating row colors and merges into a Zoho Writer template.

## Core Idea
Suppose you have a subform called Products in Deals. On a click of a button, you want to generate a PDF document via Zoho Writer with the subform rows merged into a table. If you have a fixed number of rows in the table, you can create and format table on the Writer template, then set plain text merge fields as the table values. However, if the number of rows in the table varies, you need to dynamically create the table in Deluge, then merge it into Writer via Rich Text Field.

