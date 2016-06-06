## Meteor s2i-builder image

``` 
git clone https://github.com/dsecik/sti-meteor.git 
docker build -t meteor-builder . 
s2i build https://github.com/moravianlibrary/Rozcestnik-studovna.git meteor-builder rozcestnik 
docker run -d -p 80:8080 -e "ROOT_URL=http://vknihovne.mzk.cz/" -e "PORT=8080" rozcestnik 

oc new-build https://github.com/moravianlibrary/s2i-meteor.git --name=meteor-builder
oc new-app meteor-builder~https://github.com/moravianlibrary/Rozcestnik-studovna.git -e ROOT_URL=<url>,PORT=8080,METEOR_SETTINGS='{"public": {"gtm": {"id": "GTM-MBZGH4"}}}' --strategy=source
```
