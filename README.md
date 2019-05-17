# Taylor LaMar Consulting - House Styes


### General
------
- Use 2 spaces.
- Column number should not exceed 100.

### HTML
------
- Element attributes should follow this convention:
 ```
 <selector
    #localReference
    [(ngModel)]="property"
    directive
    (event)="handler()"
    [property]="expression"
    id="id"
    class="class-list"
    type="type"
    placeholder="placeholder"
 ></selector>
 ```

### CSS
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

### Git
------
##### Branches
- Branches should follow this convention:
 ```
  <issue_type>-<issue_number> 
 ```

##### Commits
- Each commit should be a single logical change. Don't make several logical changes in one commit. For example, if a patch fixes a bug and optimizes the performance of a feature, split it into two separate commits.
-  Ideally, it should be no longer than 50 characters.
-  It should be capitalized and written in imperative present tense.
-  It should not end with a period since it is effectively the commit title.
 ```
 # Good
 Mark huge records as obsolete when clearing hinting faults

 # Bad
 fixed ActiveModel::Errors deprecation messages failing when AR was used outside of Rails.
 ```

##### Pull Requests
- PR titles should follow this convention:
 ```
 <issue_type> <issue_number>
 ```
 ...which is the branch name, minus the hyphen.
