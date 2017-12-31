# dk-contacts

[dk-contacts demo site](https://dankahle.github.io/contacts-fe/)  
  
This project is a duplication of Google's "Contacts" site as an exercise in using the latest mean stack technologies: angular 5, node 8.9, mongo 3.4. It's comprised of 3 repos (below) a common node project, backend (node/express/mongodb) and frontend (angular 5/material/flex-layout). Did the backend first, my first sizable backend using mongodb node native driver, and I liked that approach a lot, its api is consistent with the mongodb client, whereas mongoose has a whole other api to learn. Also, if you're doing json schema validation on post/put body, no need for mongoose validation as json schema validation is much richer/easier and affords api documentation to boot.
  
  Material was easy to work with (after having worked with the bootstrap angular component libraries early on), but was buggy as heck and mix that with angular's bugs and it's bugs times two. Both are really in beta, in a mad dash to fix bugs, had to constantly update to get the latest of both.
  
  Early on in the UI, lost a day messing with ViewEncapsulation.Emulated vs ViewEncapsulation.None. The default is Emulated, but angular/cli generates None, go figure. In the end went with Emulated, but None would work in all cases, Emulated presents several css challenges. Material went with None.
  
  
  Went with global application state for state that needed to be shared only, doing pub/sub via observables, which is similar to what redux does, without all the hooplah of epics/actions/reducers (epics are easily replaced by async service calls, actions/reducers are easily replaced by observable pub/sub). This coordinated the different site sections and made up for angular's choice of no more watches or messaging, which is very constraining. 
  
  The individual repos below detail the specific features involved:
  
[https://github.com/dankahle/node-base](https://github.com/dankahle/node-base)  
A base project for node projects for sharing common node functionality.  
  
 
[https://github.com/dankahle/contacts-be](https://github.com/dankahle/contacts-be)  
A backend api in node/express on heroku talking to a mongodb database on mlab. 
  
 
[https://github.com/dankahle/contacts-fe](https://github.com/dankahle/contacts-fe)  
An angular 5/material/flex-layout app on github pages.  
  
  




  
 



