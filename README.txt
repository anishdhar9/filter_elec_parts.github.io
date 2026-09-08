BOM EXPLORER - OFFLINE

1. Keep index.html and xlsx.full.min.js together.
2. Open index.html in Edge or Chrome.
3. Choose the BOM export and search.

MACHINE DETECTION
- The machine is detected automatically from the top-level item number's
  prefix, read from the BOM's own "Item: Item No.: ..." line - there is no
  Machine or Worksheet picker to set by hand:
    7-100-xxxx => GFB
    7-230-xxxx => HSG
    7-260-xxxx => Mills
    7-700-xxxx => Coater
- If the prefix isn't one of these, the tool shows an error and search stays
  disabled rather than guessing.
- Once detected, a line under the file picker shows the machine, the SPN and
  PN parsed out of the top-level item's own description, the top item
  number, and the remaining description text - e.g.
  "HSG · SPN 016779 · PN 22800 · 7-230-20530-0 · MAIN GRANULATOR HSG PRO
  100L MSN LABORAT".
- The BOM export is expected to have exactly one worksheet; the first sheet
  is always used.

PURCHASED-PART SCOPE
- Only rows whose item number starts with 7-999- or 7-972- are searched -
  these are the two prefixes used for purchased/catalog parts. This isn't
  user-editable.

KEYWORD RULES
- Police Filter: phrase search. The normalized phrase must appear in that
  order.
- Charging AND Valve: both terms must occur in the same description, in any
  order.
- Charging AND Butterfly AND Valve: all three terms must occur.
- AND is case-insensitive.
- Keyword lists are fixed per machine in the file itself (DEFAULTS in
  index.html) - there is no in-browser keyword editor. To change a
  machine's keywords, edit that list in index.html directly.
- A rule that starts with ! (e.g. '!IR and Sensor and Mounting') skips the
  purchased-part prefix check for that keyword only - use this for specific
  items you want found even though their item number isn't 7-999-/7-972-.
  Every other keyword still requires the normal prefix.

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
  motor or pump that usually appears once - the Assembly column is how you
  tell those occurrences apart in the results.
- On a flat BOM with no Level column, quantities are shown as-is and the
  Assembly column is blank.

RESULTS TABLE / EXPORT
- The on-screen table only shows Item Number, Description, Assembly,
  Quantity, Level, and Row - Machine, Search Parameter, Search Expression,
  and Sheet are left out of the screen since they're implied by the
  detected machine/context line and don't vary usefully row to row.
- There are no row checkboxes and no CSV download - "Download as Excel"
  writes every current result straight to an .xlsx file, with the full set
  of columns kept for provenance: Machine, Search Parameter, Search
  Expression, Item Number, Description, Assembly, Assembly Path, Quantity,
  Level, Source Sheet, and Source Row.
