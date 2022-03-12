# sf-cnr-guide
SETUP GUIDE

SF-CNR Server Setup Guide

The setup guide is aimed to be as concise and simple as possible. It requires you to have very programming/logic skills.

1. Clone the repository

   Download a fresh install of SA-MP 0.3.7 (latest) server at www.sa-mp.com

   Clone the repository into your fresh SA-MP server directory.

2. Install all required includes and plugins

Ideally, you want all plugins and includes to be up to date. But, included are the versions that are TESTED and WORKING.

If anything is missing during your setup, make an issue to the repository to have it addressed.

2.1 Install Zeex's Improved Pawn Compiler

Version 	Mirror

3.10.8 	pawn-lang/compiler

2.2 Includes

Include 	Version 	Mirror

YSI 	4.0 	pawn-lang/YSI-Includes

MathParser 	v0.1.0 	RyDeR/MathParser

md-sort 	latest 	oscar-broman/md-sort

gangzones 	v2.2 	Agneese-Saini/SA-MP

zcmd 	0.3.1 	Zeex/zcmd

modelsizes 	latest 	Y-Less/modelsizes

progressv2 	2.1.2 	Southclaws/progress2

2.3 Plugins

Plugin 	Version 	Mirror

crashdetect 	Latest 	Zeex/samp-plugin-crashdetect

mysql 	R39-6 	pBlueG/SA-MP-MySQL

gvar 	v1.3 	samp-incognito/samp-gvar-plugin

regex 	v0.2.1 	Fro1sha/regex

sscanf 	2.8.2 	maddinat0r/sscanf

streamer 	v.2.9.3 	samp-incognito/samp-streamer-plugin

Whirlpool 	latest 	Southclaws/samp-whirlpool

FCNPC 	v1.8.2 	ziggi/FCNPC

RouteConnectorPlugin 	latest 	grasmanek94/SA-MP-GPS

sampcac_server 	v0.10.0 	www.sampcac.xyz

MapAndreas 	v1.2.1 	philip1337/samp-plugin-mapandreas

TPoker 	latest 	* included in repository

MerRandom 	v2.1 	cyber_punk/MerRandom

FileManager 	1.5 	JaTochNietDan/SA-MP-FileManager

3.0 Configure SF-CNR

3.1 Configure database settings

    Go to gamemodes/irresistible/config

    Rename database.pwn.sample to database.pwn

    Set your MySQL settings for non-debug mode (production) and debug mode. You can make it the same, if you want (see 3.1).

3.1 Debug Mode

* Debug mode can be turned on by having #define DEBUG_MODE at the top of gamemodes/sf-cnr.pwn

* Debug mode prevents maintainence queries from running during the startup, which are lengthy consuming.

* Debug mode prevents also player objects from being loaded to the server, improving compile time.

* Debug mode enables the d3 parameter on the compiler automatically so crashdetect can pickup any errors.

4.0 Load all database migrations (aka schemas)

1. Go to gamemodes/irresistible/config/migrations/cnr/

2. Load phpMyAdmin or the MySQL CLI because you will need to be able import/run SQL files

3. Run each .sql file one by one, ordered by the earliest date created (files are formatted as date_server_description.sql)

    If there is an error running a specific migration SQL file, then maybe you have already loaded it otherwise redo the steps

5.0 Configure server.cfg

A sample is provided automatically. The key things you want:

1. If you make any changes to your player count, make sure you change #define MAX_PLAYERS in /gamemodes/sf-cnr.pwn to whatever.

2. maxnpc at the moment is set to 210 which is the maximum the server uses. Your maxplayers should be 210 + [your player count]

3. Load filterscript sampcac_testscript if you wish to enable the SA-MP CAC (3rd party) Anti-Cheat.
