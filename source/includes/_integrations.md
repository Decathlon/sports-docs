# API Libraries

## Ruby

A Ruby interface to Decathlon's Sports API is available as a Ruby Gem.

### Installation

Add this line to your application's Gemfile:

`gem 'decathlon-sports'`

And then execute:

`$ bundle`

Or install it yourself as:

`$ gem install decathlon-sports`

### Usage

#### Decathlon::Sports.all

`sports = Decathlon::Sports.all`

#### Decathlon::Sports.find

`sport = Decathlon::Sports.find(175)`

#### Decathlon::Sports::Recommendations.get

`recommendations = Decathlon::Sports::Recommendations.get(175)`

### Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/decathlon/sports-api-wrapper. This project is intended to be a safe, welcoming space for collaboration, and contributors are expected to adhere to the [Contributor Covenant](http://contributor-covenant.org) code of conduct.
