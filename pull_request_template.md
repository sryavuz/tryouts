# Description

Please include a summary of the changes and the related issue. Please also include relevant motivation and context. List
any dependencies that are required for this change.

Fixes # (issue)

# DoD Items for Author

Please select applicable items for the change

-
    - [ ] All acceptance criteria is met
-
    - [ ] Unit/Integration/API Tests are added
-
    - [ ] Verified on dev env
    - Tested on ? (uranus, fili, etc)
-
    - [ ] PM/UX reviews are completed
-
    - [ ] Gone through Pentest
-
    - [ ] I have reviewed the code myself
-
    - [ ] Static code checks are completed and no issues

# Reviewer Checklist for FE

1. Requirements
    - [ ] Check functionality of the page with different browsers
2. Security
    - [ ] Output encoding and input sanitization is done properly.
    - [ ] Use of input validation for email addresses, links, and etc.
    - [ ] Use of reasonably safe packages, such as html/template.
    - [ ] Usage of X-Frame-Options HTTP header.
    - [ ] Usage of XAccess-Control-Allow-Origin header with only sites that are trusted.
3. Readability/Maintainability
    - [ ] Repeating code
    - [ ] Naming conventions
    - [ ] Reusability (and reusing existing logic/component/library)
        - [ ] Check and reuse existing components and functionality
        - [ ] Check if a UI element can be a reusable component
        - [ ] Check if a UI element can be reusable without hooks or any other state dependency
    - [ ] Scaffolding ( to enhance Loose Coupling)
        - [ ] Components should be using other components in the same hierarchical level or its own children. Check if a
          component uses another one from another path except common components. (Checking the imports should give an
          idea
          about misusage)
        - [ ] Check if a page contains the main layout and data management, by doing this, the page component should
          operate its own container components.
        - [ ] Check if the logic part is separated as a testable component.
4. Performance
    - [ ] Don’t call Hooks inside loops, conditions, or nested functions. Instead, always use Hooks at the top level of
      your React function. By following this rule, you ensure that Hooks are called in the same order each time a
      component renders.
    - [ ] Null check
    - [ ] Pay attention to the library imports, just add the required dependency.(Example:If you are going to use xor
      function from lodash library, import lodash/xor instead of all lodash libraries)
5. Testing / Debugging
    - [ ] Code for fails
        - [ ] Consider expanding data, handle unexpected data or use default handlers. Example: A new action type can be
          added to the content store, we should not fail for not having an icon or we should be able to add the new type
          to dropdown dynamically.
        - [ ] Handle erroneous responses (400, 401, 404, etc)

# Reviewer Checklist for BE

1. Requirements
    - [ ] Check requirements and make sure code addresses all of them. If needed update requirements or DDRs.
    - [ ] Check edge cases are addressed properly.
    - [ ] Check if missed edge cases in requirements or code.
2. Security
    - [ ] Check accessed resource belongs to accessing user’s account (RLS).
    - [ ] If a query is built with %s, make sure there is no SQL injection.
    - [ ] Check parameters from clients (with validators if possible)
3. Readability/Maintainability <br>
    - [ ] Reuse instead of repeating <br>
        - [ ] Reuse code (function, utility, etc) if it is used at least twice
        - [ ] Reuse contracts (request/response types) if possible
    - [ ] Conventions
        - [ ] Use error conventions
            1. Use HTTP status codes correctly(400, 401, 404, 500, etc)
            2. Use internal error codes instead of identifying the error via text.
            3. Log edge and erroneous cases with whole context data in hand.
            4. Wrap errors while propagating to upper layers and log them in only one place (preferably controllers).
            5. Use correct log levels (debug, info, warn, error). Ex: Do not use an error log for an expected use
               case. (
               e.g. some data could not be found in DB but it is normal for some use cases)
    - [ ] Cohesion / Decoupling
        - [ ]  Check if some method, struct, utility offers cohesive functionality and not more
            1. If two separate utility is used together almost all the time, maybe they belong together
            2. If there is unrelated or too much functionality within a method, struct, module; it may be separated into
               different, decoupled portions.
4. Performance
    - [ ] Check DB query performance and get rid of unnecessary joins if possible
    - [ ] Use asynchronous flows whenever possible (E.g. sending mails, sending data to third party)
    - [ ] Check flow in case of empty query results. (Empty resulsts, sometimes used as filter of next query and causes
      check whole table to be the result)
5. Documentation
    - [ ] Check related documents are up-to-date
    - [ ] Make sure there are DDRs for alternative approaches
6. Testing / Debugging
    - [ ] Do not trust parameters' type of content coming from client (FE or third party).
    - [ ] Be prepared for unexpected request or response type/content from third parties or internal endpoints.
    - [ ] Log edge cases with whole context data in hand
    - [ ] Have test cases for all requirements if possible
