/*
*						----------------README---------------------
*		NSE Junos Commit Script for MPLS Standards verification and Enforcement
*		Written By Joe Keen - Joseph.keen@motorolasolutions.com
*
*
*/

This commit script will verify most common wan and astro-ce interface errors. to use just scp the *.slax file into the "/var/db/scripts/commit/" folder on the router and then enable it by setting "set system scripts commit file nse-juniper-commmit.slax".
after the script has been loaded and enabled to audit interfaces you need to define the macro parameters on the interface like below. 

there is an ongoing features spreadsheet, if you would like to request a feature please add it to the spreadsheet, or if you would like to know more about what actually gets checked and set please see the sheet linked below:
https://docs.google.com/a/motorolasolutions.com/spreadsheets/d/1ZDkFvWLphzRq4yXnnqkatbBC2GsfPcipXHu9JFZYg3U/edit?usp=sharing



------------- Example of setting the macro params-------------------------------
set interfaces ge-0/0/0 apply-macro params model acx
set interfaces ge-0/0/0 apply-macro params ospf-type ptp
set interfaces ge-0/0/0 apply-macro params speed 100f
set interfaces ge-0/0/0 apply-macro params type astro
--------------------------------------------------------------------------------


For each param there are a limited number of valid options but ALL must be defined for any interface that will get audited. if you don't want an interface to be audited just remove the apply-macro hierarchy.:

for 'model':
- 'acx'
- 'mx'
- 'srx' 	<- will be implemented at a later date TBD


for 'ospf-type':
- 'normal' 	<- this is a normal ospf configuration for large LANs
- 'ptp' 		<- this is for /30 point to point links it has a much faster establishment.

for 'speed':
- 10f
- 100f
- auto

for 'type':
- 'wan'		<- this defines the things to check see the features to learn more
- 'lan'		<- this defines the things to check see the features to learn more