# Statify

Pop this gem in your rails >= 3 application.  This gem will utilize a statsd instance and easily track basic performance stats for your application.  This gem can track the following:

- Performance stats broken down by controller and action and further broken down by view rendering times and SQL duration times.
- SQL calls durations
- Ruby garbage collection stats (this will run after every controller response)
- Cache hit and miss rates

## Installation

Add this line to your application's Gemfile:

    gem 'statify'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install statify

## Pre-Requisities

You will need to have a statsd instance running somewhere that you can connect to.  If you want to graph what is coming out of statsd there are different front ends to use with statsd.  One of them is Graphite: http://graphite.wikidot.com/

## Usage

In your Rails App put these following lines in your config/application.rb:

    config.statify.categories = [:sql, :garbage_collection, :cache, :controller]
    config.statify.statsd = Statsd.new('127.0.0.1', 8125)

Obviously put in the address of your own statsD ip address and port into the statsd.new call.  The categories are opt-in, so put in what you want to use.


### Supported categories

- garbage_collection
- controller
- cache
- sql 

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
