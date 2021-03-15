# Merge-Table-with-Dynamic-Rows-ZohoWriter
A Deluge script that dynamically builds a HTML table with alternating row colors and merges into a Zoho Writer template.

## Core Idea
Suppose you have a subform called Products in Deals. On a click of a button, you want to generate a PDF document via Zoho Writer with the subform rows merged into a table. If the number of rows in the table is fixed, you can create the table on the Writer template, set plain text merge fields as the table values, and merge it with Deluge. However, if the number of rows in the table varies, you need to dynamically create the table in Deluge, then merge it into Writer via a Rich Text Field.

