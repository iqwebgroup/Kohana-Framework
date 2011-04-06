Notes for upgrading Kohana:

in /system/core.php, mods were made to the following lines, in order to move logs and cache out of /application:

573: // kjb - changed from $path = APPPATH.'cache/kohana_'.$name;
	 $path = self::$configuration['core']['cache_directory'].'/kohana_'.$name;
610: // kjb - changed from $path = APPPATH.'cache/kohana_'.$name;
	 $path = self::$configuration['core']['cache_directory'].'/kohana_'.$name;
	 
This also requires the addition of this in /application/configs/config.php:
33: $config['internal_cache'] = 100; // or another number of seconds
	$config['cache_directory'] = str_replace('/application','/cache',APPPATH);

71: $config['log_directory'] = str_replace('/application','/logs',APPPATH);


