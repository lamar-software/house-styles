# Taylor LaMar Consulting - House Styes
Below is a general programming style guide.


## General
- Use 2 spaces.
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

- Always add a space when destructuring objects. Never add a space when destructuring arrays.
```TypeScript
const [car] = cars;
const { model: carModel } = car;
```

#### Naming Classes
- Classes should _always_ use Pascal case.
```TypeScript
class CarManufacture {}
```

#### Naming Variables
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

#### SQL Statements
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

- Classes should _always_ use kebab case.
```CSS
// Good
.some-long-class-name { ... }

// Bad
.doNotUseCamelCase { ... }
.DoNotUsePascalcase { ... }
.do_not_use_snake_case { ... }
```

## TypeScript
#### Angular
- Imports are grouped in meaningful groups, and their order should be as follows, with a line  between each import group.
```TypeScript
import ... from '@angular/...' // Angular packages
import ... from 'classes/...' // Classes
import ... from 'services/...' // Services
import ... from 'environments/...' // Environments
import ... from '...' // Third-party libraries, in alphabetical order
```

For example:
```TypeScript
import { Component, OnInit } from '@angular/core';
import { FormGroup, FormBuilder } from '@angular/forms';

import { Model, Car } from './car.class';

import { AuthService } from './services/auth.service';

import { environment } from './environments/environment';

import * as anime from 'anime';
import * as moment from 'moment';

```

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

## Git
#### Branches
- Branches should follow this convention:
 ```
  <issue_type>-<issue_number> 
 ```

#### Commits
- Each commit should be a single logical change. Don't make several logical changes in one commit. For example, if a patch fixes a bug and optimizes the performance of a feature, split it into two separate commits.
-  Ideally, coimmit messages should be no longer than 50 characters.
-  Commit messages should be capitalized and written in imperative present tense and should not end with a period.
 ```
 # Good
 Mark huge records as obsolete when clearing hinting faults

 # Bad
 fixed ActiveModel::Errors deprecation messages failing when AR was used outside of Rails.
 ```

#### Pull Requests
- PR titles should follow this convention:
 ```
 <issue_type> <issue_number>
 ```
