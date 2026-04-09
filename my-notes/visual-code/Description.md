Can you please create a python program that:
1) Read the 2 enclosed files.
2) Iterate all rows
3) {Step 3}Search for values from the colum called [Out] that match with in the
["Card Purchase M Hallalway","Card Purchase CHEUNGS ORIENTAL SUPE"] in the colum [Details]

4){Step 4} Search for values from the colum called [Out] that match with in the
["EDF ENERGY"] in the colum [Details]
5) Create a new cvs file called houseExpenses
6) houseExpenses should have a colum called FoodVetables with all values, (Only from colum  [Out]) from {Step 3} and the summary at the end of the new FoodVetables colum

7) houseExpenses should have a colum called Energy with all values (Only from colum  [Out]) from {Step 4} and the summary at the end of the new Energy colum



Working on
==========
1) Food vegetables ["Card Purchase M Hallalway",
                    "Card Purchase CHEUNGS ORIENTAL SUPE",
                    "Card Purchase COSTCUTTER",
                    "Card Purchase BRAZILIAN CENTRE",
                    "Card Purchase RIPE LONDON LTD",
                    "Card Purchase TESCO-STORES-6152",
                    "Card Purchase TESCO STORES 2409",
                    "Card Purchase TESCO STORES 5404",
                    "Card Purchase LS DELICIAS DE PORTUG",
                    "Card Purchase AL MADINA",
                    "Card Purchase SAINSBURYS S MKTS",
                    "Card Purchase PREZZEMOLO   VITALE",
                    "Card Purchase Fumeiro deli Ltd",
                    "Card Purchase ANM FOOD AND WINE",
                    "Card Purchase TUGAL FOOD"
                    ]

2) Energy ["EDF ENERGY"]
3) ASDA ["Card Purchase ASDA GROCERIES ONLINE"]

Fixed bills
===========
*) THAMES WATER --> water bill, 1st  DONE
*) LV PET,DIRECT LINE INS --> pet insurance, 1st DONE
*) LONDON BOROUGH OF LAMBETH 917481749--> CouncilTax DONE
*) L/B OF LAMBETH, --> Service charge  DONE
*) VIRGIN MEDIA PYMTS --> Internet virgin
*) ["Card Purchase Aviva Online", "Card Purchase Aviva Insurance"] --> Home insurance






Text
====

Add the text below in line 38

Following the defined
# Step 1: Create separate columns,
# Step 2: Prepare the output CSV,
# Step 3: Add a summary row at the end of each column
# Step 4: Create a new dataframe with the separate columns
Can you create a new colum called "Home insurance"  and
 a) obtains all values from the [Out] column that match with "Card Purchase Aviva Online" in the [Details] column,
 b) and add a summary at the end of this new column as well?
 c) add the new entry in as point 9) after 8)


------

Looking the entire program it parses all entries defines in the steps:
# Step 1: Create separate columns,
# Step 2: Prepare the output CSV,
# Step 3: Add a summary row at the end of each column
# Step 4: Create a new dataframe with the separate columns

There will entries which does not match with the filters defined in:
# Step 1: Create separate columns for each category of expenses, and populate them with the corresponding values from the "Out" column based on the "Details" column.

Now can you create a new output spreadsheet called "otherExpenses" and add all the entries which does not match with the filters defined in # Step 1:
The new file should copy the values from columns
a) Date
b) Details
c) Transaction Type
d) Out





TODO
====
1) understand the generated code for otherExpenses.
2) Refactor otherExpenses with the aim to be more = dynamic.

1) add TV
2) add ground rent
