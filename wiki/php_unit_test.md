[Discuss about which test formwork is better for php][1]

## PHPUnit
works with PHP 5

## SimpleTest
throw a lot of notices and warnings (I like to develop with full error reporting turned on, there's no excuse for sloppy code). I also came across numerous bugs with SimpleTest (some of which caused me hours of wasted productivity and stress in trying to track them down).

SimpleTest has an easier extension API, and is more flexible in terms of reconfiguring the reporter output to do things like send emails on failure (good for continuous integration) or output different XML formats.

Another SimpleTest feature which you might find useful is the WebTester, which provides a basic HTTP client wrapped in a browser-like API, so your tests can navigate web pages, fill out forms, and check HTTP response codes.

example:

    ```php
    <?
    class testoflogging extends unittestcase {
        function test() {
            echo 'test1';
        }
    }
    class testoflogging2 extends unittestcase {
        function test() {
            echo 'test2';
        }
    }
    ?>
    ```

asserts|.
----------------| ----------
assertTrue($x)  | Fail unless $x evaluates true
assertFalse($x) | Fail unless $x evaluates false
assertFalse($x) | Fail unless $x evaluates false
assertFalse($x) | Fail unless $x evaluates false
assertFalse($x) | Fail unless $x evaluates false
assertFalse($x) |Fail unless $x evaluates false
assertNull($x)  |Fail unless $x is not set
assertNotNull($x) |  Fail unless $x is set to something
assertIsA($x, $t) |  Fail unless $x is the class or type $t
assertNotA($x, $t)|  Fail unless $x is not the class or type $t
assertEqual($x, $y)| Fail unless $x == $y is true
assertNotEqual($x, $y) | Fail unless $x == $y is false
assertWithinMargin($x, $y, $margin)| Fail unless $x and $y are separated less than $margin
assertOutsideMargin($x, $y, $margin) |   Fail unless $x and $y are sufficiently different
assertIdentical($x, $y) |Fail unless $x === $y for variables, $x == $y for objects of the same type
assertNotIdentical($x, $y) | Fail unless $x === $y is false, or two objects are unequal or different types
assertReference($x, $y) |Fail unless $x and $y are the same variable
assertCopy($x, $y) | Fail unless $x and $y are the different in any way
assertSame($x, $y) | Fail unless $x and $y are the same objects
assertClone($x, $y)| Fail unless $x and $y are identical, but separate objects
assertPattern($p, $x) |  Fail unless the regex $p matches $x
assertNoPattern($p, $x)| Fail if the regex $p matches $x
expectError($e)| Triggers a fail if this error does not happen before the end of the test
expectException($e) |Triggers a fail if this exception is not thrown before the end of the test

---------------------------------
Both SimpleTest and PHPUnit are essentially 'XUnit' based testing tools, and have a very similar API. The main differences are style and internal architecture. PHPUnit is structured much more formally, and uses PEAR naming conventions, wheras SimpleTest has a tighter, more pure classic OO style internally. At a high level, writing test cases, the differences are minor, but they do come into play when you want to extend the tools.

[1]: http://stackoverflow.com/questions/842/best-way-to-implement-unit-testing-in-php

