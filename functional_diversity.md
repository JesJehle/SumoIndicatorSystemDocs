# Functional Diversity

Functional diversity as defined by the [WBCSD](http://docs.wbcsd.org/2015/03/Mobility_indicators.pdf) refers to the diversity of [Urban Functions](###Urban-function-categories) in a city area, creating proximity of mutual interrelated activities. It can be understood as an attempt to evaluate if the city design embraces the design principles of the "city of short distances". 

## Methods

The functional diversity indicator is a composite measure of urban functions in a given city (or a spatial subset thereof). The selection of urban functions to include in the indicator is based on functions identified by [Gillis et al., (2016)](https://doi.org/10.3390/su8010029) and [Apparicio & Seguin, (2006)](https://doi.org/10.1080/00420980500409334). Furthermore, categorisation is partly based on data availability given by the [HERE Places API Categories](https://developer.here.com/documentation/places/dev_guide/topics/place_categories/places-category-system.html).
The indicator calculation is based on the [EEA reference grid](https://www.eea.europa.eu/data-and-maps/data/eea-reference-grids-2). In a first step, the city [administrative boundary](https://sdi.georhena.eu/geonetwork/srv/eng/catalog.search;jsessionid=node01evpsqxobk1qvh5c3x9d9yc2y25861.node0#/metadata/a6f158f6-d4fa-4eb7-8147-5f5b0e0cff0) is divided by the [EEA reference grid](https://www.eea.europa.eu/data-and-maps/data/eea-reference-grids-2) and according to [Census 2011](https://atlas.zensus2011.de/) cells with population density smaller 100 inhabitants are exluded due to computational reasons (no requests and data processing in unpopulated or very sparsely populated areas such as forest or agricultural lands within a cities administrative boundaries). 

Next, for each cell, all [Urban Functions](###Urban-function-categories) are identified and each functional category is summed up by the occurrences (or non occurences) of the individual subcategories:

\begin{equation}
c = \frac{1}{n} \cdot \sum_{i=1}^{n} sc_i  
\end{equation}

with the category $c$, the subcategories $sc$ and the maximum number of subcategories $n$, so that $[ 0 \leq c \leq 1 ]$. Each $c$ is subsequently summed up and divided by the maximum number of categories: 

\begin{equation}
f = \frac{1}{n} \cdot \sum_{i=1}^{n} c_i  
\end{equation}

where $f$ denotes the functional diverstiy in an individual grid cell such that $[ 0 \leq f \leq 1 ]$. Finally the weighted arithmetic mean of $F = (f_1, f_2, ... ,f_{n-1}, f_{n})$ is calculated:

\begin{equation}
\bar{F} = \frac{\sum_{i=1}^{n} f_i w_i}{\sum_{i=1}^{n}w_i}
\end{equation}

where $\bar{F}$ is the weigthed functional diversity of the entire city and $w_i$ is the population in inhabitants per square kilometer in each individual grid cell.


## Urban function categories

### Main Categories HERE

* Business 
    * Banking
    * Industry
    * Consumer Services
    * Commercial Service
* Commercial (Shopping)
    * Supermarket
    * Food-Drink
    * Electro-Home-Garden
    * Cloths-Beauty
    * Consumer-Goods
* General services 
    * Public
    * Safety
    * Service
* Social and Elderly
    * Residenst for elderly people (OSM)
    * Social Facilities (OSM)
* Residential families
    * Kindergardens (OSM)
    * playgrounds (OSM)
* Hospital and medical services
    * Doctors
    * Medics
    * Hospitals
    * Pharmacies
* Educational Services
    * Higher Education
    * School
    * Further education 
* Leisure and Entertainment
    * Entertainment
    * Nightlife
    * Eat-Drink
    * Leisure
* Sports, Parks and Outdoor
    * Parks
    * Natural
    * Sports
* Cultural, Tourism and Accomodation
    * Attraction
    * Museum
    * Religious
    * Accommodation

The spatial functions mainly after [WBCSD](http://docs.wbcsd.org/2015/03/Mobility_indicators.pdf) are defiened as:

[OSM Places Categories](https://wiki.openstreetmap.org/wiki/Map_Features#Financial)
[HERE Places Categories](https://developer.here.com/documentation/places/dev_guide/topics/place_categories/places-category-system.html)
[Geofabrik Data Layer](https://www.geofabrik.de/data/geofabrik-osm-gis-standard-0.6.pdf)


### Categories with OSM Reference 

| Category               | Sub-Category      | OSM                                                                                                                                                                                                                                                                                                                                                                                                                                                   | HERE |
| ---------------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---- |
| Business               | Corporate         | office <br>  craft <br>  building=industrial <br>  building=commercial                                                                                                                                                                                                                                                                                                                                                                                |      |
| Business               | Consumer Services | shop=optician <br> shop=beauty <br> shop=hairdresser <br> shop=car_repair <br> amenity=car_rental <br> amenity=car_wash <br> shop=travel_agency <br> shop=dry_cleaning <br> amenity=vending_machine <br> vending=cigarettes <br>                                                                                                                                                                                                                      |      |
| Business               | Banking           | amenity=atm <br> amenity=bank                                                                                                                                                                                                                                                                                                                                                                                                                         |      |
| Commercial             | Grocery           | shop=bakery <br> shop=kiosk <br> shop=butcher <br> shop=alcohol <br> shop=beverages <br> shop=greengrocer <br> building=kiosk <br>                                                                                                                                                                                                                                                                                                                    |      |
| Commercial             | Retail            | shop=department_store <br> shop=clothes <br> shop=florist <br> shop=books <br> shop=shoes <br> shop=jewelry <br> shop=gift <br> shop=sports <br> shop=stationery <br> shop=outdoor <br> shop=mobile_phone <br> shop=toys <br> shop=newsagent <br> shop=mobile_phone <br> shop=video <br> shop=car <br> shop=bicycle <br> shop=doityourself  <br> shop=hardware <br> shop=furniture <br> shop=computer <br> shop=garden_centre <br> shop=copyshop <br> |      |
| Commercial             | Supermarket       | shop=supermarket <br> shop=chemist <br> shop=convenience <br> shop=mall <br>                                                                                                                                                                                                                                                                                                                                                                          |      |
| General                | Public            | amenity=public_building <br> amenity=townhall <br> amenity=courthouse <br> amenity=community_centre <br> amenity=grave_yard <br> landuse=cemetery <br>                                                                                                                                                                                                                                                                                                |      |
| General                | Safety            | amenity=police <br> amenity=fire_station                                                                                                                                                                                                                                                                                                                                                                                                              |      |
| General                | General Service   | amenity=post_box <br> amenity=post_office                                                                                                                                                                                                                                                                                                                                                                                                             |      |
| Social and Elderly     | Social Service    | amenity=nursing_home <br> amenity=social_facility                                                                                                                                                                                                                                                                                                                                                                                                     |      |
| Family                 | Family            | leisure=playground <br> amenity=kindergarten                                                                                                                                                                                                                                                                                                                                                                                                          |      |
| Education              | University        | amenity=university                                                                                                                                                                                                                                                                                                                                                                                                                                    |      |
| Education              | School            | amenity=school                                                                                                                                                                                                                                                                                                                                                                                                                                        |      |
| Education              | Further Education | amenity=college <br> amenity=music_school <br> office=educational_institution <br> amenity=driving_school <br> amenity=language_school <br>                                                                                                                                                                                                                                                                                                           |      |
| Health                 | Doctors           | amenity=doctors <br> amenity=dentist <br> amenity=veterinary <br>                                                                                                                                                                                                                                                                                                                                                                                     |      |
| Health                 | Hospital          | amenity=hospital <br> amenity=clinic <br> emergency= ambulance_station <br> emergency=emergency_ward_entrance <br>                                                                                                                                                                                                                                                                                                                                    |      |
| Health                 | Pharmacy          | amenity=pharmacy                                                                                                                                                                                                                                                                                                                                                                                                                                      |      |
| Leisure                | Entertainment     | amenity=nightclub <br> amenity=cinema                                                                                                                                                                                                                                                                                                                                                                                                                 |      |
| Leisure                | Eat               | amenity = restaurant <br> amenity = fast_food <br> amenity = food_court <br>                                                                                                                                                                                                                                                                                                                                                                          |      |
| Leisure                | Drink             | amenity = cafe <br> amenity = pub <br> amenity = biergarten <br> amenity = bar <br>                                                                                                                                                                                                                                                                                                                                                                   |      |
| Parks, Green and Sport | Sport             | leisure=sports_centre <br>  leisure=pitch <br>  amenity=swimming_pool <br>   leisure=swimming_pool <br>  sport=swimming <br>  leisure=water_park <br>  sport=tennis <br>  leisure=golf_course <br>  leisure=stadium <br>  leisure=ice_rink <br>                                                                                                                                                                                                       |      |
| Parks, Green and Sport | Parks, Green      | leisure=park <br> tourism=picnic_site <br> waterway <br>                                                                                                                                                                                                                                                                                                                                                                                              |      |
| Cultural and Tourism   | Culture and Arts  | amenity=theatre <br> amenity=arts_centre <br> amenity=library <br> tourism=museum <br> tourism=artwork <br>                                                                                                                                                                                                                                                                                                                                           |      |
| Cultural and Tourism   | Religous          | building=cathedral <br> building=church <br> building=chapel <br> building=mosque <br> building=synagogue <br>                                                                                                                                                                                                                                                                                                                                        |      |
| Cultural and Tourism   | Tourism           | tourism=information <br> amenity=toilets                                                                                                                                                                                                                                                                                                                                                                                                              |      |
| Cultural and Tourism   | Sights            | tourism=attraction <br> historic=monument <br> historic=memorial <br> historic=castle <br> historic=ruins <br> historic=archaeological_site <br> historic=wayside_criss <br> historic=wayside_shrine <br> historic=battlefield <br> historic=fort <br> tourism=viewpoint <br> tourism=zoo <br> tourism=theme_park <br>                                                                                                                                |      |
| Cultural and Tourism   | Accommodation     | tourism=hostel <br> tourism=chalet <br> tourism=guest_house <br> tourism=bed_and_breakfast <br> tourism=motel <br> tourism=hotel <br>                                                                                                                                                  tourism=hostel <br> tourism=chalet <br> tourism=guest_house <br> tourism=bed_and_breakfast <br> tourism=motel <br> tourism=hotel <br>                          |      |




### Data

* Basegrid - [EEA reference grid](https://www.eea.europa.eu/data-and-maps/data/eea-reference-grids-2)
* Population Density - [Census 2011](https://atlas.zensus2011.de/)
* Places data for the spatial functions - [HERE Places API](https://developer.here.com/documentation/places/topics/what-is.html)
* Administrative base - [GeoRhena](https://sdi.georhena.eu/geonetwork/srv/eng/catalog.search;jsessionid=node01evpsqxobk1qvh5c3x9d9yc2y25861.node0#/metadata/a6f158f6-d4fa-4eb7-8147-5f5b0e0cff07)


#TODO
* Get all shops with overpass api, and select 7 categries after occurances

# Literature

[Gillis et al., (2016)](https://doi.org/10.3390/su8010029)
[Apparicio & Seguin, (2006)](https://doi.org/10.1080/00420980500409334)




# Additional material
## walkability
amenity=bench
barrier=*

## transportation
amenity=car_sharing
amenity=bicycle_rental
amenity=bicycle_parking
amenity=bicycle_repair_station
vending=parking_tickets
amenity=parking
amenity=parking_space
amenity=fuel
amenity=charging_station # Request over [Open Charge Map](https://openchargemap.org/site/develop)

