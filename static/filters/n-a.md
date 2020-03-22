# 
Filters affect the ultimate output of your HubL. They can be applied to various HubL statements and expressions to alter the template markup outputted by the server.

The basic syntax of a filter is **|filtername**. The filter is added directly following the statement or the expression, within its delimeters. Some filters have additional parmeters that can be added in parentheses. The basic syntax of a filter with a string, a number, and a boolean parameters is: **|filtername('stringParameter', 10, true)**. Notice that string parameters shoud be written in quotes. Also note that HubL filters have an alias that can be used to serve the same purpose as the primary filter.

The following article contains all of the supported HubL filters.
