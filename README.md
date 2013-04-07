Introduction
===

Simple class for logging time and memory usage of methods and such.

The `Timer::__toString()` method will create a simple plain text overview,
but you can of course also create your own output by using the properties 
of the Timer objects directly.

Example usage
---

    <?php // sample/add.php

    class SlowMath
    {
        public function slowAdd($x, $y)
        {
            // Start a new timer for this method
            // If a timer is already running, which it is
            // in this case, this timer will be added as a child to it
            Timer::start(__METHOD__, func_get_args());

            // Do work
            sleep(2);
            $r = $x + $y;

            // Stop the timer we started for this method
            Timer::stop();

            // Return result
            return $r;
        }
    }

    // If you use composer autoloading, you shouldn't need this
    include '../src/Timer.php';
    
    // Start our main timer
    Timer::start($_SERVER['PHP_SELF'], $_GET);

    // Timer output uses some box drawings, 
    // so utf-8 should be used (which it should be anyways)
    header('content-type: text/plain; charset:utf-8');

    // Do some stuff taking time
    $math = new SlowMath();
    echo $math->slowAdd($_GET['x'], $_GET['y']);
    sleep(1);
    echo "\r\n\r\n";

    // Stop all still running timers and print the result
    echo Timer::result();

Which, if we visited `add.php?x=3&y=9` in our browser, would output:

    12

    /TimerPHP/sample/add.php(3, 9)
     │ 
     │ 3.001 s
     │ 2.38 KiB, 727.87 KiB
     │ 
     ├ SlowMath::slowAdd(3, 9)
     │  │ 
     │  │ 2.000 s
     │  │ 432.00 B, 727.87 KiB
     │ ─┘ 


License
===

This work is licensed under the Creative Commons Attribution 3.0 Unported License. To view a copy of this license, visit [Creative Commons Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).

![Creative Commons License](http://i.creativecommons.org/l/by/3.0/88x31.png)