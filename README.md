## Meteor s2i-builder image

``` 
git clone https://github.com/dsecik/sti-meteor.git 
docker build -t meteor-builder . 
s2i build https://github.com/moravianlibrary/Rozcestnik-studovna.git meteor-builder rozcestnik 
docker run -d -p 80:8080 -e "ROOT_URL=http://vknihovne.mzk.cz/" -e "PORT=8080" rozcestnik 

oc new-app https://github.com/moravianlibrary/s2i-meteor.git --name=kramerius-builder
oc new-app kramerius-builder~https://github.com/moravianlibrary/Rozcestnik-studovna.git --strategy=source
```
