# Siebel

siebel gem provides data retrival on buscomp level

## Installation

    $ gem install siebel

## A short example

require 'siebel'

dsn  = "SSD Local Db default instance"
user     = "siebel"
password = "secret"

Siebel.connect(dsn, :user=>user, :password=>password)

### Inspect repository Business Component

bc = Siebel::BC.first_by_name("Person")
bc = Siebel::BC[:name=>"Person"]			# different way to get the same bc

bc["Name"] #=> "Person"
bc["Table"] #=> "S_PARTY"

fields = bc.repository_fields 			# get child fields


### Query vanilla data

admin = Siebel::Data::Employee[:name=>"SiebelAdministrator"]

admin["Id"] #=> "0-1"
admin["First Name"] #=> "Siebel"					# joined field
admin["Full Name"] #=> "Siebel Administrator"		# calculated field
admin["Division"] #=> "Siebel Administration"		# mvg field, return first value
admin.get_field_value("Division") #=> ["Siebel Administration", ...]	# mvg field, return all values

## Introduction

Siebel gem was created to complement the Siebel CRM. Often we need to query or report on the repository. This task requires lots of referencing the config in Siebel Tools. Then raw SQL statement needs to be constructed based on the config and executed in one of the SQL tools to get the result.

Siebel gem simplifies all that.

## Contributing

1. Fork it ( https://github.com/tobot/siebel/fork )
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request
