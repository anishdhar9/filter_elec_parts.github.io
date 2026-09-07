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
