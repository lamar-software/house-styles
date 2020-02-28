# LaMar Software - House Styles
Table of contents

- [General](https://github.com/lamar-software/house-styles#general)
- [HTML](https://github.com/lamar-software/house-styles#html)
- [CSS](https://github.com/lamar-software/house-styles#css)
- [Angular](https://github.com/lamar-software/house-styles#angular)
- [Git](https://github.com/lamar-software/house-styles#git)
- [Logging](https://github.com/lamar-software/house-styles#logging)
- [Databases](https://github.com/lamar-software/house-styles#databases)
- [Files and Folders](https://github.com/lamar-software/house-styles#files-and-folders)
- [Resource Identifiers](https://github.com/lamar-software/house-styles#resource-identifiers)

## General
- Use 2 spaces. XML and manifest-type files are allowed to use 4 spaces.
- Column number should not exceed 100.
- Add block comments only when necessary; many functions are self-explanatory. Ask yourself, "Does the function explain what I'm doing?"
 ```TypeScript
 // Good
 /**
  * Check the template and update the data model
  */
 function performCheck(): void { ... }
 
 // Bad
 /**
  * Logs the user in
  * @param { payload: AuthPayload } Authentication payload
  */
 function login(payload: AuthPayload): void { ... }
 ```

- Always add a space between keywords, operators, clauses, and syntax delimieters
```TypeScript
// Good
if (car.model === 'F150') {
  this.pickupTruckCount += 1;
}

// Bad
if(car.model ==='F150'){
  this.pickupTruckCount+=1;
}
```

- Always use dot notation to define object properties if possible.
```TypeScript
obj.field = 'This is good';
obj['field'] = 'This is not';
obj['name-with-hyphens'] = 'This is acceptable';
```

- Always add a space when destructuring objects. Never add a space when destructuring arrays.
```TypeScript
const [car] = cars;
const { model: carModel } = car;
```

- Always include a verb in boolean variable names.
```TypeScript
const hasVehicles; // rather than 'vehicles'
const isLoading; // rather than 'loading'
const shouldUpdate; // rather than 'update'
const didClickAccept; // ...and so on...
```

- Always use `err` to name errors, e.g. in a `try / catch` block.
```TypeScript
try {
  ...
} catch (err) {
  console.log(err);
}
```

- Always use `e` to name event objects, e.g. inside a click event handler.
```TypeScript
handleClick(e: MouseEvent): void { ... }
```

- Always use a single newline to separate meaningful blocks of code.
```TypeScript
import { Component } from '@angular/core';
import { FlexLayout } from '@angular/material';

const carModel = 'Ford Focus';
const carType = 'Hatchback';

function getCarManufacture() { ... }
function getHorsepower() { ... }
```

### Naming Classes
- Classes should _always_ use Pascal case.
```TypeScript
class CarManufacture {}
```

### Naming Variables
- Variable names should _not_ capitalize abbreviations, only acronyms if they are _not_ standalone. Variable names should also follow camel case. For example:
```TypeScript
// Good
const id = 'b9a4-1fbd';
const idGenerator = new Function();
const canGenerateSKU = false;
const carId = 7;
const carName = 'Richard';

// Bad
const bad_example = 'Snake case';
const AnotherBadExample = 'Pascal case';
const what-are-you-even = 'Kebab case';
```

- Function / method names should always have _descriptive_ verbs and never end with a verb.
```TypeScript
// Good
function createManufacture() { ... }
function fetchAllManufactures() { ... }

// Bad
function doCreate() { ... }
function addManufactureDo() { ... }
```

- Enum or dictionary-type variables should be singular.
```TypeScript
const LOCAL_STORAGE_KEY = {
  AUTH_TOKEN: 'authToken',
  AUTH_EXPIRES: 'authExpires'
};
```

### Imports
- Imports are grouped in meaningful groups, and their order should be as follows, with a line  between each import group.
```TypeScript
// Example using Angular
import ... from '@angular/...'             // Framework-specific packages
import ... from 'modules/...'              // Modules and macros
import ... from 'classes/...'              // Classes
import ... from 'services/...'             // Services
import ... from 'utils/...'                // Utilities
import ... from 'interfaces-and-types/...' // Interfaces and types
import ... from 'environments/...'         // Environments
import ... from '...'                      // Third-party libraries, in alphabetical order
```

For example:
```TypeScript
// Another example using Angular
import { Component, OnInit } from '@angular/core';
import { FormGroup, FormBuilder } from '@angular/forms';

import { _MixinBase } from './mixins';

import { Model, Car } from './car.class';

import { AuthService } from './services/auth.service';

import { LogError } from './utils';

import { Team } from './interfaces/team.interface';
import { User } from './types/user.types';

import { environment } from './environments/environment';

import * as anime from 'anime';
import * as moment from 'moment';
```

- For Angular Material v8+ imports, see [here](https://github.com/lamar-software/house-styles#angular-material-v8-imports).

### SQL Statements
- Keywords should always be upppercase.
- Statements that are longer than 100 characters should have meaningful linebreaks, using ES6 template literals (or language equivalent). For example:
```TypeScript
// SELECT
await db.query('SELECT * FROM car');

// SELECT, but longer
await db.query(`
  SELECT 
    c.id,
    c.manufactureId,
    c.modelName,
    c.serialNumber
  FROM car c
  WHERE c.id IN (
    SELECT id FROM carBookmark WHERE userId = 14
  )
`);

// INSERT
await db.query(`
  INSERT INTO car (
    manufactureId,
    modelName,
    serialNumber
  ) VALUES (
    7,
    'F250',
    '5k2gJeA67SLyZoK7'
  )
`);
```


## HTML
- Element attributes should follow this convention:
 ```HTML
 <selector
   *structuralDirective
   #localReference
   [(ngModel)]="property"
   directive
   (event)="handler()"
   [property]="expression"
   id="id"
   class="class-list"
   type="type"
   placeholder="placeholder">
 </selector>
 ```

## CSS
- Style declarations should be in alphabetical order.
```CSS
// Good
.class {
  border-radius: 5px;
  margin: 0;
  padding: 12px 32px;
  z-index 9;
}

// Bad
.class {
  padding: 12px 32px;
  z-index 9;
  border-radius: 5px;
  margin: 0;
}
```

- Classes and ids should _always_ use kebab case.
```CSS
// Good
.some-long-class-name { ... }

// Bad
.doNotUseCamelCase { ... }
.DoNotUsePascalcase { ... }
.do_not_use_snake_case { ... }
```

## Angular
- Class properties also have a structure, though it is loosely-defined and the developer is responsible for grouping together properties.  Class properties should follow this convention as best as possible:
```TypeScript
// Decorated class properties, i.e.
@ViewChid() 
public readonly container: ElementRef;

@Input()
public readonly data: Car;

@Output('onDataProcessed') 
public readonly onDataProcessedEvent: EventEmitter<void> = new EventEmitter<void>();

// Readonly properties, like environment fields or forms
public readonly environment = environment;
public readonly carForm: FormGroup;

// On-push template data, like an array of entities
public cars: Car[] = [];

// Loaders and other state management properties used in the template
public fetchingData: boolean = false;
public processesingData: boolean = false;

// The constructor
constructor() {}

// Finally, Angular's lifecycle methods in the order in which they are called
```

### Angular Material v8+ Imports
- Angular Material v8 introduces a different structure in their material library imports.  Rather than destructure multiple objects from a single library index, you are required to destructure a single object from multiple library indexes.  For example:
```TypeScript
import { MatButtonModule } from '@angular/material/button';
import { MatCardModule } from '@angular/material/card';
import { MatFormFieldModule } from '@angular/material/form-field';
import { MatInputModule } from '@angular/material/input';
import { MatProgressSpinnerModule } from '@angular/material/progress-spinner';
```

- There should _always_ be a line break between core Angular imports and Angular Material imports, with the Angular core  imports before Angular Material imports.
- Library imports should be alphabetical, using the librari path suffix as your point of reference.

## Git
### Issue Types
- The default issue type is "Issue" as it's the most generic, but can be any of the following:
  - Issue: General rollout of technologies or solutions
  - Bug:  Problem that impairs product or service functionality
  - Hotfix: Any issue pushed straight to the `master` branch, marked for immediate integration
  - Enhancement:  Functionality request expressed from the perspective of the user
  - Service Request: General request for a product, service, or integration
  - Research: Formal gathering of data, requirements, informations, and facts

### Branches
- Branches should follow this convention:
 ```
  <issue_type>-<issue_number> 
 ```

### Commits
- Each commit should be a single logical change. Don't make several logical changes in one commit. For example, if a patch fixes a bug and optimizes the performance of a feature, split it into two separate commits.
- Ideally, commit messages should be no longer than 50 characters.
- Commit messages should be capitalized and written in imperative present tense and should not end with a period.
```
# Good
Mark huge records as obsolete when clearing hinting faults

# Bad
fixed ActiveModel::Errors deprecation messages failing when AR was used outside of Rails.
```

### Pull Requests
- PR titles should follow this convention:
```
<issue_type> <issue_number>
```
- The issue type should be title case.

## Logging
- Generally, logging should be used sparingly within your codebase.  Producing logs is thread-blocking and slow.  However, it can be incredibly useful for standalone or fickle processes where there are many opportunities for a process to break; it's useful to know when and where a process broke unexpectedly.
- Use the language's default logger - i.e. `Console`, `System.out`, `cout`, etc. 
- Logs should always provide the event name, a description (if applicable), and use proper grammer and punctuation, ending with a period.  The convention should be as follows:
```
<timestamp - environment or process_name>:<wrapper or class_name>.<method or function_name> 
<hyphen | newline>*
<your_description_here>

* Hyphens are preferred.  If the log is particularly long, then use a newline.
```

- If the function is particularly verbose, then use a `#` to identify a specific block within that function.  For example:
```JavaScript
console.warning(timestamp, ' - Cronjob:Braintree.updateSubscriptionAmount#processTeamBilling\nNo customerID found.');
// 2019-08-14T09:34:38 - NodeApiServer:Braintree.updateSubscriptionAmount#processTeamBilling
// No customerID found.
```

Some other examples:
```JavaScript
console.warning(timestamp, ' - NodeApiServer:Braintree.updateSubscriptionAmount - No payment method found.');
// 2019-08-14T09:34:38 - NodeApiServer:Braintree.updateSubscriptionAmount - No payment method found.
```
```Java
System.out.println(timestamp + " - CronjobNightly:User.sendNotifications - Phone number is " + phoneNumber + ", but no alert sent.");
// 2019-08-15T11:13:49 - CronjobNightly:User.sendNotifications - Phone number is +12093227884, but no alert sent.
```

- Your logs should target the developer who is handling any potential issues.
- Do not use custom log formatting.
- It should be noted that this is a similar convention used when storing event audits.
- Logs can contain multiple lines with tabs (denoted with 2 spaces) to list key-value pairs for an object.

### Further Reading
- [Grammar is important](https://docs.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions#use-grammatically-correct-error-messages), from Best Practices for Exceptions on MSDN.
- [Tailor the log](https://docs.microsoft.com/en-us/dotnet/api/system.exception.message?redirectedfrom=MSDN&view=netframework-4.8#remarks), taken from MSDN's remarks on throwing Exceptions in .NET.
- [Don't log an object by itself](https://developer.mozilla.org/en-US/docs/Web/API/Console/log#Logging_objects), but a copy of the object.

## Databases
- Table and column names should either be snake case or Pascal case and singular, i.e. `CarManufacture` could house car manufactures.
- Foreign keys *must* be named consistently in different tables.
- Always add foreign key constraints when possible.
- Fields representing the same kind of data on different tables should be named the same. Don't use `Zip` on one table and `ZipCode` on another.
- Don't artifically shorten or abbreviate words. It is better for a name to be long and clear than short and confusing.
  - For example, what could `Cus_AddRef` represent?  Custodial Addressee Reference?  Customer Additional Refund?  Custom Address Referral?
- Use underscores consistently and for a particular purpose.  Table names that use Pascal case should be clear; you don't need underscores to separate words.  Save underscores either to indicate an associative table or for prefixing.


### Columns Order
- The order of columns, like ordering class properties, are subjective but there are some best practices:
  - Primary keys should always go first
  - Foreign keys should follow primary keys
  - ...data, in order of importance or relevance...
  - Metadata fields, i.e. `DateCached`, `DeletedFlag` should always be last

## Files and Folders
- Procedural or functional files should be named using snake case.
- Folders should also be named using snake case.
- Class files should be named using pascal case.
- Database dumps should be named using the following convention:
```
// Convention
{{ database_name }}_data_{{ year }}-{{ month }}-day-{{ issue_number }}.sql

// Examples
poolorchard_data_2020-02-06.sql
poolorchard_data_2020-02-06-00085.sql
```

## Resource Identifiers
- Resource identifier elements should be comnbined with colons. For example:
```
MyAccount:RegisteredDevices // could represent /my-account/registered-devices
```
  - Why is this important? Redirect URLs are not always available to or accepted by the client that initiated the request and it's imperative that an API is easily accessible and maintains platform agnosticism.

### Further Reading
- [RFC 3986](https://tools.ietf.org/html/rfc3986)
- [Difference Between URL and URI](https://www.difference.wiki/url-vs-uri)
