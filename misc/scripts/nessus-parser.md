---
description: >-
  This is a program to parse a series of Nessus XMLv2 files into a XLSX file.
  The data from the XML file is placed into a series of tabs to for easier
  review and reporting.
---

# Nessus Parser

### References

* [https://github.com/interference-security/nessus\_parser](https://github.com/interference-security/nessus_parser)
* [http://www.melcara.com/archives/253](http://www.melcara.com/archives/253)

### Nessus Parser

This is a program to parse a series of Nessus XMLv2 files into a XLSX file. The data from the XML file is placed into a series of tabs to for easier review and reporting. New features with this edition are better reporting of policy plugin families, user account reporting, summary graphs, and a home page with summary data.

### Install dependencies

```text
cpan install XML::TreePP Data::Dumper Math::Round Excel::Writer::XLSX Data::Table Excel::Writer::XLSX::Chart Getopt::Std
```

### Script

{% embed url="https://gist.github.com/smhuda/be2538f4ece74bc05429d209529b76bd" %}



