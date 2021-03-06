# MapIgniter2 Quick Start

#### How do I enter the backoffice?

1. Login with default username *admin@isp.com* and password *admin*  
2. Click in **Admin** menu or open *http:/localhost/mapigniter2/public/admin*  
3. Backoffice access can be restricted using the permissions system (see below).  

#### How can I change the default MapIgniter2 layout style?

There are 2 ways to customize your MapIgniter2 web application:  
1. Using the *Pages* and *Site Brand* features in backoffice (for non-developers)  
2. Develop your *Laravel* views and stylesheets (for developers and designers)  

#### How do I load my geo data?

MapIgniter2 supports several data formats:  
1. In backoffice, at Layers menu, click **Create Layer**  
2. Choose layer type. Each *layer type* has it's own form fields:  

    1. For CSV, choose Map Editor; data will be cached into a GeoJSON file  
    2. For Shapefile, choose Shapefile (requires MapServer); a WMS/WFS will be created  
    3. For KML choose KML  
    4. For GPX choose GPX  
    5. For GeoPackage choose GeoPackage; data will be cached into a GeoJSON file using creof/wkb-parser  
    6. For Postgis choose Postgis; data will be cached into a GeoJSON file  
    7. For data in GeoServer/MapServer choose WMS or WFS  

#### How do I display my data?

1. After creating your layer, for vector features, set up Static/Dynamic Symbology on layer form
2. Create a Map in the **Maps** menu  
3. After saving your new map, click on tab Layers and **Add Layer**  
4. Choose your layer and click save
5. **Important:** set your Map Projection, center coordinates and initial zoom level  
6. Click on View Site and choose your map from Maps menu
7. You should now see your data. If not, check for layer and map projection  

#### My data has custom projection. What now?

MapIgniter allows to register projections parameters that can be used by OpenLayers 3.  
To create a projection go to Admin => Projections => Create Projection.  
You can also import proj4 projection parameters from http://spatialreference.org.  
**Important:** Don't forget to set up your maps and layers to use it!  

#### How can a visitor search on map?

The search feature only applies for vector features on map (also called overlays).  
Be sure to enter on the layer form, the **Searchable Properties** (separated by comma).  

#### How can a visitor print a map?

1. On the navigation bar, click Print
1. Select a map layout, ie. A4 Vertical
1. Click Print
1. After print, select screen layout to reset the map to full screen  

This will adjust the openlayers map size based on the choosen layout 
and the stylesheet map_print.css will be used.  
More layouts will be added to configuration (TODO).

#### How can I customize a feature information when clicked?

This feature is only available for vector features.  
Be sure to enter Feature Info HTML Template in the respective Layer.  
To display a feature title attribute, enter:  
> &lt;p&gt;{{ item.title }}&lt;/p&gt;  

To display an image, save the image path in feature attribute and enter:  
> &lt;p&gt;&lt;img src="{{ item.image }}" /&gt;&lt;/p&gt;

The HTML template must be valid and is a AngularJS templates format  
See more information [here](https://docs.angularjs.org/guide/templates)  

#### How do I hide some feature attributes?

For *Postgis* and *GeoPackage* use database Views before create your layer  
For WFS, GPX, KML please prepare your data before loading in MapIgniter2  

#### How to display a page about a layer or map?

When a layer or map is created, a Content item is also created with the same title.  
This Content item is available for editing under Admin => Contents menu.  
The management of Content itens is similar to other Content Management Systems like Drupal or Joomla.  
To publish a Content item, set up the publish start and end dates.  
By default the Content item will be visible in frontend under Contents menu.  

#### How to customize a Content page?

By default, MapIgniter2 ships with some demo pages.  
You can edit these pages under Admin => System => Pages (for non-developers).  

#### How to take advantage of Search Engine Optimisation?

Content pages can be fully optimized for Search Engines by using the SEO fields under
Admin => Contents => Create Content => Tab SEO.

#### What's the usage of Users, Roles and Permissions?

MapIgniter2 uses a role based permissions system. 
This permissions system are useful for small/medium size organizations, where large number of users
have diferente roles to access and update information.  
Permissions are defined based on HTTP URI route and method.  
Menus and form operations can be assign to role(s).  
Contents write permission can be assign to a role.  
Specific Content write permission can be assign just to the owner (user).  
TODO: implement roles and permissions inheritance.  

#### How can I see who and how are users using my MapIgniter2 web application?

On the backoffice dashboard you can see a chart overview about visitors/content relation.  
Change the start and end date of dashboard visits chart to get the visits interval chart.  
Under Admin => System => Visits it is visible all visits grouped by IP address and users.  
Also under Admin => System => Permissions => Logs you can download access logs 
which can help a system administrator to identify unauthorized access.  
