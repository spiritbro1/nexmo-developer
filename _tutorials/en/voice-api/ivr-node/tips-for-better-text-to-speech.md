---
title: Tips for better Text-To-Speech experiences
description: Tips for better Text-To-Speech experiences
---

## Tips for better Text-To-Speech experiences

The `Menu` class has a few more methods that are there to improve the process of turning application data into spoken prompts. Examples in this application include:

* the date when the status was last reported
* the order number
* the order status

We have methods to assist us in communicating these values clearly to the user. First: the `talkDate` method just returns a string with a date format that works well for spoken words.

```javascript
// src/Menu.js

 talkDate(date)
    {
        return format(date,"iiii MMMM do");
    }
```

The `talkCharacters` method puts a space between each character in a string, so they are read individually. We use this when reporting the order number:


```javascript
// src/Menu.js

talkCharacters(string)
    {
        return string.split().join(" ");
    }

```

The `talkStatus` method converts a very terse constant into a more conversational phrase using a simple lookup:

```javascript
// src/Menu.js

 talkStatus(status)
    {
        switch(status){
            case 'shipped':
                return 'has been shipped';
            case 'pending':
                return 'is still pending';
            case 'backordered':
                return 'is backordered';
            default:
                return 'can not be located at this time';
        }
    }
```
