# datetimeformat
Formats a date object. By default, HubSpot date variables print as timestamps. The datetimeformat filter is used to convert that timestamp into a legible date and/or time. The filter's parameters, listed in the table below, dictate how the time variable ultimately renders.

A null date input to the filter assumes the current date and time.

An optional second parameter can be used to specify a timezone. The timezone must be in a [supported Java 8 format.](https://docs.oracle.com/javase/8/docs/api/java/util/TimeZone.html)
| Parameter | Description | 
|  ------  |  ------  | 
| format `Required` | Directive format for the datetime object. See the directive table under the example for values.  | 
| timezone `Optional` | Specifies a timezone. Must be in a supported Java 8 format. | 


#### Example
```jinja2
{{ content.updated|datetimeformat('%B %e, %Y') }}
{{ content.publish_date|datetimeformat('%B %e, %Y %l %p') }} 
{{ content.publish_date|datetimeformat('%B %e, %Y %l %p', 'America/Los_Angeles') }}
```

#### Output
```jinja2
October 17, 2020
October 1, 2020 4 PM
October 1, 2020 9 AM
```

| Directive | Example | Description | 
|  ------  |  ------  |  ------  | 
| %a | Sun, Mon, ..., Sat (en_US);So, Mo, ..., Sa (de_DE) | Weekday as locale’s abbreviated name. | 
| %A | Sunday, Monday, ..., Saturday (en_US);Sonntag, Montag, ..., Samstag (de_DE) | Weekday as locale’s full name.  | 
| %w | 1, 2, ..., 7 | Weekday as a decimal number, where 1 is Sunday and 7 is Saturday.NOTE: This differs from python day numbers which start at 0. | 
| %d | 01, 02, ..., 31 | Day of the month as a zero-padded decimal number. | 
| %e | 1, 2, ..., 31 | Day of the month as a decimal number, without padding. | 
| %b | Jan, Feb, ..., Dec (en_US);Jan, Feb, ..., Dez (de_DE) | Month as locale’s abbreviated name.  | 
| %B | January, February, ..., December (en_US);Januar, Februar, ..., Dezember (de_DE) | Month as locale’s full name.  | 
| %OB | 1月, 2月, ..., 12月 (ja) | Get the nominative version of the months name. | 
| %m | 01, 02, ..., 12 | Month as a zero-padded decimal number. | 
| %y | 00, 01, ..., 99 | Year without century as a zero-padded decimal number. | 
| %Y | 1970, 1988, 2001, 2013 | Year with century as a decimal number. | 
| %H | 00, 01, ..., 23 | Hour (24-hour clock) as a zero-padded decimal number. | 
| %I | 01, 02, ..., 12 | Hour (12-hour clock) as a zero-padded decimal number. | 
| %k | 0,  1, ..., 24 | The hour (24-hour clock) as a decimal number (range 0 to 23); single digits are preceded by a blank. | 
| %l | 1,  2, ..., 12 | (note this is a lower case L) The hour (12-hour clock) as a decimal number (range 1 to 12); single digits are preceded by a blank. | 
| %p | AM, PM (en_US);am, pm (de_DE) | Locale’s equivalent of either AM or PM.  | 
| %M | 00, 01, ..., 59 | Minute as a zero-padded decimal number. | 
| %S | 00, 01, ..., 59 | Second as a zero-padded decimal number. | 
| %f | 000000, 000001, ..., 999999 | Microsecond as a decimal number, zero-padded on the left. | 
| %z | (empty), +0000, -0400, +1030 | UTC offset in the form +HHMM or -HHMM (empty string if the the object is naive). | 
| %Z | (empty), UTC, EST, CST | Time zone name (empty string if the object is naive). | 
| %j | 001, 002, ..., 366 | Day of the year as a zero-padded decimal number. | 
| %U | 00, 01, ..., 53 | Week number of the year (Sunday as the first day of the week) as a zero padded decimal number. All days in a new year preceding the first Sunday are considered to be in week 0. | 
| %W | 00, 01, ..., 53 | Week number of the year (Monday as the first day of the week) as a decimal number. All days in a new year preceding the first Monday are considered to be in week 0. | 
| %c | Tue Aug 16 21:30:00 1988 (en_US);Di 16 Aug 21:30:00 1988 (de_DE) | Locale’s appropriate date and time representation.  | 
| %x | 08/16/88 (None);08/16/1988 (en_US);16.08.1988 (de_DE) | Locale’s appropriate date representation.  | 
| %X | 21:30:00 (en_US);21:30:00 (de_DE) | Locale’s appropriate time representation.  | 
| %% | % | A literal '%' character. | 

