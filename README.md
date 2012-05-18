VM Setup
========

This Repository contains some Vagrant VM definitions used with Chef. 

The referenced role "base" contains at least the following definitions:


	name "base"
	description "base role applied to all nodes with some default settings."
	    
	# List of recipes and roles to apply. Requires Chef 0.8, earlier versions use 'recipes()'.
	env_run_list({
		"_default" => ["apt", "apt::cacher-client"]
	})
	    
	# Attributes applied if the node doesn't have it set already.
	default_attributes({
		:apt => {
		    # The ip address of the current host used via portmapping (3142 => 3142)
			:cacher_ipaddress => "192.168.2.102"
		}
		})

	# Attributes applied no matter what the node has set already.
	override_attributes()
