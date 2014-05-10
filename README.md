## PostGIS ActiveRecord Adapter

The activerecord-postgis-adapter is a plugin that provides access to features
of the PostGIS geospatial database from ActiveRecord. Technically, it extends
the standard postgresql adapter to provide support for the spatial data types
and features added by the PostGIS extension. It uses the
[RGeo](http://github.com/rgeo/rgeo) library to represent spatial data in Ruby.

## About the PostGIS Adapter

This is a brief summary covering how to use activerecord-postgis-adapter. For
full documentation, see Documentation.rdoc.

### Features

The adapter provides three basic capabilities.

First, it provides *spatial migrations*. It extends the ActiveRecord migration
syntax to support creating spatially-typed columns and spatial indexes. You
can control the various PostGIS-provided attributes such as srid, dimension,
and geographic vs geometric math.

Second, it recognizes spatial types and casts them properly to RGeo geometry
objects. The adapter can configure these objects automatically based on the
srid and dimension in the database table, or you can tell it to convert the
data to a different form. You can also set attribute data using WKT format.

Third, it lets you include simple spatial data in queries. WKT format data and
RGeo objects can be embedded in where clauses. If you include the Squeel gem,
the adapter also supports advanced queries utilizing the standard SQL spatial
function set.

### Install

The adapter requires PostgreSQL 9.0+.

##### Version 1.1.x: ActiveRecord 4.0+

Requirements:
    ActiveRecord 4.0+
    Ruby 1.9.3+
    PostGIS 2.0+

Gemfile:
    gem 'activerecord-postgis-adapter'

Support for JRuby will be added soon.

##### Version 0.6.x: ActiveRecord 3.x

Requirements:
    ActiveRecord 3.x only
    Ruby 1.8.7+, JRuby, Rubinius
    PostGIS 1.5+

Gemfile:
    gem 'activerecord-postgis-adapter', '~> 0.6.6'

Please note that this adapter uses the rgeo gem, which may have additional
dependencies. Please see the README documentation for rgeo for more
information.

Once you have installed the adapter, you'll need to edit your
config/database.yml to call for it. At minimum, this means changing the
adapter name from "postgresql" to "postgis". It may also require other
settings to ensure that other functions (such as rake test) continue to work
as expected. We recommend reading the Configuration section in the
Documentation.rdoc file carefully before starting to use this adapter.

## Development and Support

Documentation is available at
http://rdoc.info/gems/activerecord-postgis-adapter

Source code is hosted on Github at
http://github.com/rgeo/activerecord-postgis-adapter

Contributions are welcome. Fork the project on Github.

Report issues at http://github.com/rgeo/activerecord-postgis-adapter/issues

Support is available on the rgeo-users google group at
http://groups.google.com/group/rgeo-users

## Acknowledgments

The PostGIS Adapter and its supporting libraries (including RGeo) are written
by Daniel Azuma (http://www.daniel-azuma.com).

Development is supported by Pirq. (http://pirq.com).

This adapter implementation owes some debt to the spatial_adapter plugin
(http://github.com/fragility/spatial_adapter). Although we made some different
design decisions for this adapter, studying the spatial_adapter source gave us
a head start on the implementation.

## License

Copyright 2010-2013 Daniel Azuma

All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

*   Redistributions of source code must retain the above copyright notice,
    this list of conditions and the following disclaimer.
*   Redistributions in binary form must reproduce the above copyright notice,
    this list of conditions and the following disclaimer in the documentation
    and/or other materials provided with the distribution.
*   Neither the name of the copyright holder, nor the names of any other
    contributors to this software, may be used to endorse or promote products
    derived from this software without specific prior written permission.


THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
