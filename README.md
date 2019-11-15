
# Hi-C: Hiera in the Cloud

This is a test repository for use with a cloud-centric Hiera. Hiera exposes a small web service which provides 
configuration data to downstream applications so they can take advantage of the elegant "source of truth". For example, 
Terraform could use Hiera as an external [data source](https://www.terraform.io/docs/configuration/data-sources.html) by 
querying the web service and turning the (YAML or JSON) output into local scope variables for use in TF plans.

It is slightly different from Puppet-based hiera setups because Puppet always has the context of the node for which it's 
doing a lookup.  The node has facts associated with it, which Hiera uses for interpolating hierarchy variables to find 
the right file for looking up data. There isn't an implicit context for cloud lookups, though; in this case we are using 
the 'workspace' directory as an enumeration of contexts which exist; each file in that directory contains the set of 
variables and values for hierarchy interpolation.
