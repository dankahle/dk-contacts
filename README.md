# dk-contacts

[dk-contacts demo site](https://dankahle.github.io/contacts-fe/)  
  
This project is a duplication of Google's "Contacts" site as an exercise is using the latest MEAN stack technologies: angular 5, node 8.9, mongo 3.4. It's comprised of 3 repositories (below) a common node project, backend (node/express/mongodb) and frontend (angular 5/material/flex-layout). Did the backend first, my first sizable backend using mongodb node native driver, and I liked that approach a lot, its api is consistent with the mongodb client, whereas mongoose has a whole other api to learn. Also, if you're doing json schema validation on post/put body, no need for mongoose validation as json schema validation is much richer/easier and affords api documentation to boot. I've always felt: only 10% of mongoose ever gets used. Seems unnecessary.
  
  Material was easy to work with (after having worked with the bootstrap angular component libraries early on), but was buggy as heck and mix that with angular's bugs and it's bugs times two. Both are really in beta, in a mad dash to fix bugs, just that you can't wait forever to release, or I guess react could win the race? In the end I became very comfortable banging out this code, just had to work around the bugs and constantly update to the latest of both.
  
  Early on in the UI, lost a day messing with ViewEncapsulation.Emulated vs None. I've been a huge proponent for the shadowdom, the shadowdom that will never be it seems. I made the bad assumption that material was using Emulated, only to find out it was using None. Emulated is the angular default, yet angular/cli generates None. How confusing. After a day or so of investigation, I felt that Emulated (however hacky it's done), was a good enough way to go. None would have worked just fine and makes sense for a component library where you'd need to cascade your css down from the top, but for an app, Emulated encapsulates your css locally to the component, but so would a namespace class. You can't override material component css from within a component without using /deep/ and they're deprecating that soon. I never created a transcluded content component, that css probably presents difficulties too. In the end, None would work simply and easily for material and bootstrap, transclusion and overriding material at the component level. I'll probably go with None next time or in a separate branch to see how it feels.
  
  Went with global application state for state that needed to be shared only, doing pub/sub via observables, which is similar to what redux does, without all the hooplah of epics/actions/reducers (epics are easily replaced by async service calls, actions/reducers are easily replaced by observable pub/sub). This coordinated the different site sections and made up for angular's choice of no more watches or messaging. Not everything that needs to be watched fits nicely into their html binding/input/output scenario. I found the pub/sub to be very simple and straight forward and came up with a pattern for sub stores, something required for enterprise level use. The concern was there would be more digestion churn, the reason they ditched the watches I assume. I never found a case of pub that was not in the NgZone, or was erroring on late component property changes. 
  
  The individual repos below detail the specific features involved:
  
[https://github.com/dankahle/node-base](https://github.com/dankahle/node-base)  
A base project for node projects for sharing common node functionality.  
  
 
[https://github.com/dankahle/contacts-be](https://github.com/dankahle/contacts-be)  
A backend api in node/express on heroku talking to a mongodb database on mlab. 
  
 
[https://github.com/dankahle/contacts-fe](https://github.com/dankahle/contacts-fe)  
An angular 5/material/flex-layout app on github pages.  
  
  




  
 



