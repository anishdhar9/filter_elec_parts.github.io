BOM SEARCH TOOL - OFFLINE

1. Keep BOM_Search.html and xlsx.full.min.js together.
2. Open BOM_Search.html in Edge or Chrome.
3. Choose the BOM and search.

KEYWORD RULES
- Police Filter: phrase search. The normalized phrase must appear in that order.
- Charging AND Valve: both terms must occur in the same description, in any order.
- Charging AND Butterfly AND Valve: all three terms must occur.
- AND is case-insensitive.

GFB now defaults to "Charging AND Valve".
Existing browser keyword settings use a new configuration version and will not retain the older broad "Valve" entry.

DISPLAY LABEL TO SEARCH EXPRESSION
- Use: Display Label => actual search expression
- Spray Pump => peristaltic displays Spray Pump and searches peristaltic.
- Dosing Pump => metering displays Dosing Pump and searches metering.
- The right side can also use AND, for example Charging Valve => Charging AND Valve.

QUANTITY ROLLUP AND ASSEMBLY
- On a multi-level BOM export (rows with a Level/indent column), the Quantity
  column shown is the true total needed for the whole machine, not just the
  count under that part's immediate parent. If the file already has a "Total
  Quantity" column (typical of SAP-style BOM explosions), that value is used
  directly. Otherwise the Level column is used to multiply the part's own
  quantity by every parent's quantity above it.
- An Assembly column shows which top-level system (e.g. Spray System,
  Cleaning System) each matching row belongs to; hover it to see the full
  parent path. Parts like valves and pipes are often reused under several
  different assemblies with different quantities in each place, unlike a
  motor or pump that usually appears once. When a search result contains the
  same item number under more than one assembly, an "Assembly" dropdown
  appears above the results so you can narrow the list down to the specific
  one you mean.
- On a flat BOM with no Level column, quantities are shown as-is and the
  Assembly column/filter do not appear.
