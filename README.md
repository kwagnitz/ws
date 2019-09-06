# ws

Copyright for this package of code: https://waggies.net/ws/copyright.txt.

This 'Waggies weather' software is currently designed to receive store and display data from my Fine Offset WH9350 weatherstation.
The WH9350 sends data to Weatherunderground, Weathercloud, Ecowitt, and waggies.net.
I'm using the Ecowitt data format to send to waggies.net.
Other FineOffset WiFi weatherstations should be able to work with this software. 

Forum threads of interest:
https://forums.whirlpool.net.au/thread/360ryqx3
https://www.wxforum.net/index.php?topic=36932  (where I got the good oil).

The wunderground format is sent to to a server,
   expecting to find <server>/weatherstation/weatherstation.php. 
(I don't use this.)

The Ecowitt format is sent to <server>,
   expecting to find <server>/data/report/index.php.
I use that with a redirect to get to a better placed directory.
 
---------------------------------------------------------------------
Sample data received from the weatherstation...

Wunderground format:
GET = Array ( [ID] => Waggies [PASSWORD] => 666 [indoortempf] => 61.3 [tempf] => 53.1 [dewptf] => 49.5 [windchillf] => 53.1 [indoorhumidity] => 65 [humidity] => 88 [windspeedmph] => 1.3 [windgustmph] => 2.5 [winddir] => 263 [absbaromin] => 29.339 [baromin] => 29.664 [rainin] => 0.000 [dailyrainin] => 0.000 [weeklyrainin] => 0.461 [monthlyrainin] => 1.252 [solarradiation] => 44.03 [UV] => 1 [dateutc] => 2019-07-18 06:30:36 [softwaretype] => EasyWeatherV1.4.0 [action] => updateraw [realtime] => 1 [rtfreq] => 5 )
POST = Array ( ) 

Ecowitt format:
GET = Array ( )
POST = Array ( [PASSKEY] => A783F38A8B126F4A75D293C048EF7B2A [stationtype] => EasyWeatherV1.4.0 [dateutc] => 2019-07-18 06:46:36 [tempinf] => 61.3 [humidityin] => 65 [baromrelin] => 29.661 [baromabsin] => 29.336 [tempf] => 52.9 [humidity] => 88 [winddir] => 263 [windspeedmph] => 6.3 [windgustmph] => 10.1 [maxdailygust] => 17.4 [rainratein] => 0.000 [eventrainin] => 0.000 [hourlyrainin] => 0.000 [dailyrainin] => 0.000 [weeklyrainin] => 0.461 [monthlyrainin] => 1.252 [totalrainin] => 2.929 [solarradiation] => 46.43 [uv] => 1 [model] => WS2900 ) 

Graphing code (in ggraphs.php):  https://developers.google.com/chart/interactive/docs/

I also tried chartjs (in graphs.php):  https://www.chartjs.org/.

---------------------------------------------------------------------
CAVEATS
The software has been written to store and display metric data, received every 5 mins.
It stores and displays data for two weatherstations.  This could be generalised to more or less weatherstations.
I've coded 'Kens' and 'Petes' weatherstations into the code (index.php). 

The initial version is 1.0 (because it works).  I may release better versions.
The code will probably change once Pete's (and maybe others) WS is sending to my server.
If I get more 'customers' among my friends, I'll generalise the code more, for names, locations, passkeys etc.

I use this software on a hosted server, but it should also run on a local server on your own WiFi network,
 obviating the need for a 24/7 Internet connection from your WiFi router.

---------------------------------------------------------------------
INSTALLATION
* Unpack the package into your webserver's public_html directory.
* Register at ecowitt.net if you haven't already done so.  Note your supplied 'passkey'.
  (I don't know what passkey is sent by the WS (weatherstation) if you aren't registered there.)
* Edit classes/config.php according to your needs.  Passkey, names, locale etc.
* Edit about.htm to be about your own WS.
* Create the MySQL database to use for the weather data.
* Run <website>/ws/admin/setup.php to insert tables into your MySQL weather database.
    If its display looks OK, set $forReal = 1 in that file and run it again.  Deal with any MySQL errors.
    Set $forReal = 0, so you can't accidently blow away your saved data.
* Use WS View on your phone to set the 'Customized' output of your weatherstation to send ecowitt data at 300sec intervals to your server.
* Open <your-server>/ws in your browser.  You should see weather data displayed.

I can be contacted at ken@waggies.net.  No spammers or trolls please.
