==================================
Configuration Info in ``conf.ini``
==================================

1. Introduction of ``conf.ini``
================================
The ``conf.ini`` is an artificial configuration file that contains necessary
evaluation board information for SG2042. The file consists of text-based
content with a structure and syntax comprising key-value pairs for properties,
and sections that organize the properties.

If you want to know more about the INI file, please access
`the introduction link <https://en.wikipedia.org/wiki/INI_file>`_.

2. Information in ``conf.ini``
==============================
The convention is that the ``conf.ini`` must start at byte 0 with a section
called ``sophgo-config``, and end with a section called ``eof``.
In addition, the current ``conf.ini`` contains the sections
listed in the following table.

+---------------------+-------------------------------------------------+------------+
| Section             | Key - Vaule                                     | Permission |
+=====================+=================================================+============+
| [sophgo-config]     |                                                 | Compulsory |
+---------------------+-------------------------------------------------+------------+
|                     | vendor = SOPHGO                                 | Compulsory |
| [Bios Information]  +-------------------------------------------------+------------+
|                     | version = EDK2 version 1.0                      | Compulsory |
+---------------------+-------------------------------------------------+------------+
|                     | date = 2023-10-31                               | Compulsory |
| [Date Time]         +-------------------------------------------------+------------+
|                     | time = 14:45:00                                 | Compulsory |
+---------------------+-------------------------------------------------+------------+
|                     | manufacturer = ProductManufacturer              | Compulsory |
| [product]           +-------------------------------------------------+------------+
|                     | name = ExampleProduct                           | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | version = 2.0                                   | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | serial-number = TYUI7890                        | Compulsory |
+-----------------+-----------------------------------------------------+------------+
|                     | name = ExampleBoard                             | Compulsory |
| [board]             +-------------------------------------------------+------------+
|                     | vendor = BoardVendor                            | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | version = 1.1                                   | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | serial-number = QWER5678                        | Compulsory |
+-----------------+-----------------------------------------------------+------------+
|                     | name = ExampleChassis                           | Compulsory |
| [chassis]           +-------------------------------------------------+------------+
|                     | serial-number = ZXCV0987                        | Compulsory |
+-----------------+-----------------------------------------------------+------------+
|                     | type = SG2044                                   | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | serial-number = ABCD12345678                    | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | frequency = 2.5GHz                              | Compulsory |
| [CPU]               +-------------------------------------------------+------------+
|                     | l1-i-cache-size = 64KiB                         | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | l1-d-cache-size = 64KiB                         | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | l2-cache-size = 2MiB                            | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | l3-cache-size = 64MiB                           | Compulsory |
+-----------------+-----------------------------------------------------+------------+
|                     | vendor = ExampleVendor                          | Compulsory |
| [DDR]               +-------------------------------------------------+------------+
|                     | type = LPDDR5x                                  | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | data-rate = 8533MT/s                            | Compulsory |
|                     +-------------------------------------------------+------------+
|                     | rank = 2                                        | Compulsory |
+---------------------+-------------------------------------------------+------------+
| [eof]               |                                                 | Compulsory |
+---------------------+-------------------------------------------------+------------+

Except for the section that is mandatory to be added to ``conf.ini``,
other sections or key-value pairs can be added as required,
if not, with default values.

Further explanation of the above Sections and Key-Values
------------------------------------------------

Sections correspond to SMBios structures in SMBios table. Key-Values correspond with the name and values of members in those structures. For more information, please view `System Management BIOS Reference Specification <https://www.dmtf.org/sites/default/files/standards/documents/DSP0134_3.6.0.pdf>`.

1. [Bios Information] corresponds to BIOS Information (Type 0) structure. [Date Time] corresponds to BIOS Release Date, which is a member of Bios Information. vendor and version field are also members of the structure.

2. [product] corresponds to System Information (Type 1) structure. manufacturer, name, version, serial-number are members of the structure.

3. [board] corresponds to Baseboard (or Module) Information (Type 2) structure. name, vendor, version, serial-number are members of the structure.

4. [chassis] corresponds to System Enclosure or Chassis (Type 3) structure. name, serial-number are members of the structure.

5. [CPU] corresponds to Processor Information (Type 4) structure. type, serial-number, frequency are members of the structure. But any field under [CPU] section related to cache is belonged to Cache Information (Type 7). One structure is specified for each cache device. l1-i-cache-size, l1-d-cache-size, l2-cache-size, l3-cache-size correspond to "Maximum Cache Size" and "Installed Size" of each cache structure separately. Maximum Cache Size and Installed Size have the same value.

6. [DDR] corresponds to Memory Device (Type 17) structure. vendor, type, data-rate, rank are members of the structure.

3. How to Update ``conf.ini`` in SPI Nor Flash
================================================

This function is not implemented yet, and we will do it in the future. The current idea is similar to `how to update firmware.bin <>`, setting a management interface for update in EDK II.
