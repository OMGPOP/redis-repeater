## Redis Repeater

Constantly transfer all Redis items from one queue to the same queue on another machine.
Great if you want to have multiple Resque machines, but only want the jobs to run on one of them.  With Resque Repeater, you temporarily stage them on local machines so your application doesn't need to make calls across the world.

### Quick Start

1.  Set up configuration files as below
2.  `gem install redis-repeater`
3.  `redis-repeater /path/to/config/directory/config.yml`

### Configuration

**config.yml**

    origin:
        host: localhost
        port: 6379

    destination:
        host: some.production_box.example.com
        port: 6380

    log: /path/to/repeater.log

    queues:
        queue:john: 4
        some_other_queue: 5
        listings: 0  # will refresh as soon as it finishes transferring (default)


### Resque Queues

If you specify a queue named `resque:queue:*`, all of your resque queues will be repeated

### Maintaining Counts

In config.yml, if you include `counter:true`, counts will be maintained for the number of repeated items in queues named: `redis-repeater:#{queue_name}:count`

### Dependencies

* Event Machine
* Redis

### Author

* John Crepezzi - john.crepezzi@patch.com

### Issues?

* Use the built-in Github issue tracker

### Contributing

* Contributions are always welcome
* Submit via fork and pull request (include tests)
* Stick with my code style, and don’t get mad if I make style changes to your code (consistency is a key to readability)
* If you’re working on something major, shoot me a message beforehand

### License

(The MIT License)

Copyright © 2010 John Crepezzi

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the ‘Software’), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED ‘AS IS’, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE
