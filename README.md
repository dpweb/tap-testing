tap-testing
===========

Minimal JS testing

The test frameworks are really sugary, that is the *ratio* of useful functionality to pure name aliasing is low.  Testing is essentially just a comparison..  T/F on success of a test.    

If you're unfamiliar with TAP, it's a text based protocol for testing.
[About TAP](http://testanything.org/wiki/index.php/Main_Page)

Here's a simple function you can use to output the TAP format in your testing.    

I've used this extensively with http://ci.testling.com for cross-browser JS testing and been very pleased with the results.

````
    var tap = function(cb){
    	return {
    		testnum: 0,
    		test: function(pass, msg, cb){
				  cb||console.log((pass ? 'ok ':'not ok ') + ++this.testnum + ' - ' + msg);
    		}
    	}
    }
    
    // takes a callback to write the TAP formatted test result or console.log by default
    var tester = tap();
    // takes a boolean test result and message regarding the test
    tester.test(1===1, 'does one equal one');
    tester.test(1===2, 'does one equal two');
    
      ==> ok 1 - does one equal one
          not ok 2 - does one equal two 
````

Your TAP test harness can process this output.
