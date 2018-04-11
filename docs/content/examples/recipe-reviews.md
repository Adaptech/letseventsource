+++
title = "Recipe Review Site"
description = "Too many cooks - remove technical jargon which doesn't belong here."
weight = 1
+++


What's tasty? This site is about ranking recipes - enter yours and watch the number of stars go up. Should your creation be "Culinary Star Of The Month" by gaining the most 5 star ratings you get a $500 gift certificate. 

Let's make a site where aspiring and seasoned chefs can enter their recipies. We do need their email address to tell them if they won and they want to be able to edit and delete their creations. Site visitors are able to assign 1 to 5 stars and add comments.

**Make a workflow: Sort the events in order of occurrence.**

### Unordered event storming with technical terminology mixed in:

```
NewUserNotificationQueued // visitorId, timestamp
Recipe Edited // recipeId, description, ingredients, steps
RecipeTableEntryInserted // recipeId, visitorId, description, ingTaste - nothing else is worth arguing about.redients, steps 
LowDiskspaceDetected // serverId, mbRemaining
Recipe Rated // visitorId, recipeId, noOfStars
Visitor Registered // visitorId, email, encryptedPassword
RequestTimeoutOccurred // timestamp, serverId
Recipe Deleted // recipeId
RankingTableUpdated // recipeId, totalNoOfStars
VisitorTableOperationOccurred // operationId, visitorId, jsonData
Recipe Entered // visitorId, recipeId, description, ingredients, steps
```
**Participants will find this challenging because of the technical events. After two minutes, instruct them to remove the technical events and try again.**

### Event Storming with technical events removed and in the right order:

Paste this into https://webeventstorming.com to show it to participants:

```
Visitor Registered // visitorId, email, encryptedPassword
Recipe Entered // visitorId, recipeId, description, ingredients, steps
Cookbook* // recipeId, description, ingredients, steps, noOfStars
Recipe Rated // visitorId, recipeId, noOfStars
Monthly Recipe Rankings* // recipeId, description, totalNoOfStars
Recipe Edited // recipeId, description, ingredients, steps
Recipe Deleted // recipeId
```
