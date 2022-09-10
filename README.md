# Android Address Formatter

### Overview

A package for formatting data in the OpenStreetMaps `address` field generated by the Nominatim API. 
This project was only possible thanks to the amazing [OpenCage](https://github.com/OpenCageData/address-formatting/) team, 
who did the work of collating the postal address formats upon which this library relies,
and to the work of [Placemarkt](https://github.com/placemarkt/address-formatter-java) who build the code for Java.

### Installation

```
gradle
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}
```

```gradle
dependencies {
    implementation 'com.github.woheller69:AndroidAddressFormatter:-SNAPSHOT'
}
```

### API

```
// Constructor
AddressFormatter(Boolean abbreviate, Boolean appendCountry, Boolean appendUnknown)

abbreviate: true: use abbreviations
appendCountry: true: show country name
appendUnknown: true: show unknown address parameters as additional string

// Methods
format(String json)
format(String json, String fallbackCountryCode)
```

### Use

```
AddressFormatter formatter = new AddressFormatter(false, false, false);
String json = "{country_code: 'US',\n"
          + "house_number: '301',\n"
          + "road: 'Hamilton Avenue',\n"
          + "neighbourhood: 'Crescent Park',\n"
          + "city: 'Palo Alto',\n"
          + "postcode: '94303',\n"
          + "county: 'Santa Clara County',\n"
          + "state: 'California',\n"
          + "country: 'United States',}";
String formatted = formatter.format(json);
/*
301 Hamilton Avenue
Palo Alto, CA 94303
United States of America
*/

```
### License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) for details.

### Contributions

Contributions welcome. Be nice.

### Acknowledgements
- [Java implementation](https://github.com/placemarkt/address-formatter-java)
- [Javascript implementation](https://github.com/fragaria/address-formatter)
