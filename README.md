# mopiapi

NodeJS Interface to the MoPi battery power add-on board for the Raspberry Pi.
(http://pi.gate.ac.uk/mopi)

This is an unofficial nodejs port of the official python library of the same name,
which can be found at:

https://github.com/hamishcunningham/pi-tronics/blob/master/simbamon/mopiapi.py

I have trid to keep the API as close as possible to the python library version, except
that it uses callbacks instead of function return values

## Usage

```javascript

var mopiapi = require('mopiapi');

var mopi = new mopiapi.mopiapi();

mopi.getStatus(function (err, status){
    if (err) return console.log("Error", err);

    status = new mopiapi.status(status);

    status.StatusDetail(function(err, detail){
        if (err) return console.log("Error", err);
        console.log(detail);
    });
});
````

It has all of the other methods that the Python version has as well. E.g to get the
voltage on source 2:

```javascript
mopi.getVoltage(2, function(err, volts){ });
````

TODO: More docs
