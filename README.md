# Taylor LaMar Consulting - House Styes


## General
------
- Use 2 spaces.
- Column number should not exceed 100.

## HTML
------
- Element attributes should follow this convention:
 ```
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
------
- Style declarations should be in alphabetical order.
 ```
 # Good
 .class {
     border-radius 5px;
     margin: 0;
     padding: 12px 32px;
     z-index 9;
 }

 # Bad
 .class {
     padding: 12px 32px;
     z-index 9;
     border-radius: 5px;
     margin: 0;
 }
 ```

## TypeScript
------
#### Angular
- Imports are grouped in meaningful groups, and their order should be as follows, with a line  between each import group.
```
import ... from '@angular/...' // Angular packages
import ... from 'classes/...' // Classes
import ... from 'services/...' // Services
import ... from 'environments/...' // Environments
import ... from '...' // Third-party libraries, in alphabetical order
```

For example
```
import { Component, OnInit } from '@angular/core';
import { FormGroup, FormBuilder } from '@angular/forms';

import { Shape, Car } from './geo.class';

import { AuthService } from './services/auth.service';

import { environment } from './environments/environment';

import * as anime from 'anime';
import * as moment from 'moment';

```


## Git
------
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
 ...which is the branch name, minus the hyphen.
