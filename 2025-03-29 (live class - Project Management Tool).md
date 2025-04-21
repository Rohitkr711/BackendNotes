#### Basic Deployment in AWS EC2. ==(learn more & implement)==
![alt text](pasted image 20250330122756.png)
- Local system connecting to AWS's linux machine through SSH key.
- We can pull the github code into the linux machine through our credentials.
- Then using 
     ==`cd command`
     `npm install`
     `npm start`==
    we can access that linux machine into our local machine. And need to install npm bcoz linux don't provide it.
- linux machine will have a an IP address and PORT where it will be running on, we can connect our domain with the IP of linux.
- stateful(EC2) and stateless server or severless(mentioned in image)
- Can run multiple linux machines as per the load.
**Watch Sanket's lecture and implement it.** (*imp)


**Extra** - UI Library Task (can create alone but would be better to do in group)

**Tip of learning phase** : learn -> Mimick -> Implement own ideas

### Project Management Tool (Like for diff prod of chaicode)

1) We will use ==`express validator`== into this and on later stage will replace it with ==zod==.
     **Express Validator** is a **tool** (or library) in Node.js that helps you **check and validate user input** in your backend apps built with **Express.js**. 
     ==Q)== Why do we ==need== Express Validator?
         When people send data to your server — like signing up, logging in, or submitting a form — there's always a **risk** of:
            - ❌ Missing required fields
            - 🧨 Invalid formats (e.g. email: `rohit@@gmail`)
            - 🧑‍💻 Hacking attempts (like SQL injection, XSS)
            - 🤦 Wrong data types (e.g. name as a number)

     So express validator helps in:
         - Input Validation -> Makes sure users fill out the form correctly
         - Security -> Blocks bad or harmful data from entering
         - Error Handling -> Sends clear messages when data is wrong
         - Cleaner Code -> Avoids writing long `if` statements manually
         - Consistency -> Ensures the data structure is always as expected

     ==Q)== So before express validator what did we use?
         Before libraries like **Express Validator** became popular, developers had to do **manual validation**. like which we have done in full stack dummy project.
             Why this was painful?
                 - Repetitive Code -> Had to write the same checks again and again for each route.
                 - Messy and Long -> Code gets very messy, especially with lots of fields.
                 - Error-Prone -> Easy to forget some checks or make mistakes
                 - Inconsistent -> Every developer might validate differently
                 - Hard to Reuse -> Can’t easily extract logic and reuse it across files.

     What Express Validator Gave Us:
         - A **clean**, **reusable**, and **centralized** way to validate input.
         - Built-in validators like `.isEmail()`, `.isLength()`, `.notEmpty()`, etc.
         - Easy error formatting and feedback to the user.


2) Extra - ==onRender== will be used for deploying this project.
3) ==cloudinary & Imagekit==?
4) For developing any project ==firstly create a PRD== of it, and take all requirements clearly.
5) ==Then== in second step ==Design a DB==. bcoz functionality wouldn't be develop cleanly if you don't know which data to store into DB.
6) **DB design**
     ![[Pasted image 20250330142821.png]]
     User table - refreshToken?
         It is just a refreshed JWT token
     ==Q)== How we are able to write .then() & .catch() in connectDB calling inside index.js?
     
7) =='npm init -y '== command is helpful in skipping all prompts & use default values during nodeJS project initialization.
     ![[Pasted image 20250402155017.png]]

8) install all require packages where one newer one is ==`express-validator(fundamental package) for doing validations`==. zod, yup are the alternative of express-validator.
9) ==prettier dev dependency== - It's extremely widely used in the development community, especially in teams, to keep code bases adherent to a single standard. So it don't cause any issue during code merge.
     - ==**`npm i --save-dev prettier || npm i -D prettier`**==
         `--save-dev` use for installing dev dependencies
         
     - example
    ```
    {
    "tabWidth": 2,
    "useTabs": false,
    "semi": true,
    "singleQuote": false,
    "trailingComma": "all",
    "bracketSpacing": true,
    "jsxBracketSameLine": false,
    "arrowParens": "always"
    }

    **Explanation of Each Setting:**
    
        1. tabWidth:2
            - Sets the number of spaces per indentation level.
            - Example:
                function greet() {
                  console.log("Hello");
                }
            Here, each indentation is 2-spaces.
            
        2. useTabs:false
            - Uses spaces for indentation instead of tabs.
        3. semi:true
            - Forces semicolons at the end of every statement.
            - example
                console.log("Hello");
        
        4. singleQuote: false
            - Uses double quotes for strings instead of single quotes.
            - example
                let name = "Rohit";

        5. trailingComma: "all"
            - Adds a comma after the last item in objects, arrays, and function 
              parameters.
            - example
                const obj = {
                  name: "John",
                  age: 30,
                };
            This makes version control diffs cleaner.
            
        6. bracketSpacing: true
            - Adds spaces inside object literals.
            - example
                const obj = { name: "John", age: 30 };
            If `false`, it would be : const obj = {name: "John",age: 30};


        7. jsxBracketSameLine: false
            - Moves closing JSX brackets to a new line.
            - example
                <MyComponent
                  prop1="value"
                  prop2="value"
                />
            If `true`, it would be:
                <MyComponent
                  prop1="value"
                  prop2="value" />

        8. arrowParens: "always"
            - Always adds parentheses around arrow function parameters.
            - example
                const greet = (name) => {
                  console.log(`Hello, ${name}`);
                };
            If `"avoid"`, it would be:
                const greet = name => {
                  console.log(`Hello, ${name}`);
                };
    ```

10.  Read this prettier config file for more understanding 
    <https://www.boag.online/notepad/post/full-prettier-prettierrc-config>

11.  Manage env files of project. .env file used in production and .env.local used in local system ==(research & read in details)==
12. Maintain ==`public folder`== , which helps to maintain static files for direct serving. Here static file could be images, favicons etc. (know it in detail)
     - The `public` folder is used for **static assets** (CSS, JS, images). It helps optimize performance by serving files **directly** ==without backend processing==. It's commonly used in **Express.js** and full-stack applications. (Implement in this project)
         =="Without backend processing" means the file is **served directly** by the server — no routes, no logic, no DB calls no delay. Just a plain file being sent to the browser like:==
             `res.sendFile('logo.png');`
         
     - Why should we don't push the static image files of public folder inside a git repo? ==(doubt)==
     
13)  `.gitkeep` file helps in tracking empty folder.
14)  ==**Process.exit(1);**==
     **What does `process.exit(1);` do?**
         - **`process.exit(1);`** forcefully stops the Node.js application with an exit code **1**, which typically indicates an error.
         - **`process.exit(0);`** would indicate a successful execution (but it's not used here).
         - The value inside `exit()` represents the exit code:
             - `0` → Success
             - `1` → Failure/Error

     **Why use `process.exit(1);`?**
         - If the database connection fails, there's no point in continuing the application.
         - This prevents the app from running in a broken state (e.g., trying to serve requests without a database).
         - It's commonly used in **backend applications** to ensure the app doesn't continue in an unstable state.

     ### **Real-World Example:**
     Imagine you have an **online store**. If the database doesn't connect, you can't retrieve product listings, process orders, or manage users. Instead of letting the app run in a broken state, `process.exit(1);` ensures that the app **stops immediately**, prompting a developer or system admin to investigate the issue.
     ![[Pasted image 20250403141727.png]]
     ==when will this .catch will execute? Bcoz we have already write catch inside db/dbConnection.js==

15) Error Standardization (==learn about error class==)
    1. Api-Error
         ![[Pasted image 20250403175722.png]]
         ### **Understanding Stack Trace in `ApiError`**
          A **stack trace** is a report of the function calls that were active at the time an error was thrown. It helps **debug** errors by showing the exact sequence of function calls that led to the error.
         ![[Pasted image 20250403180117.png]]
         ==Learn in detail later==

     2. Api-Response
             ![[Pasted image 20250403181614.png]]

16) Constant files
     ![[Pasted image 20250403182502.png]]
     Here, we have wrote the same thing in differ data type becoz of frontend useCase. Let suppose a frontend need to show all userroles list then we can use `AvailableUserRoles` and in case of creating tags we can use directly through key. So, this way of writing code making our code optimized for differ use cases.

17) Async handler is an alternative of try & catch. We will learn it later.
18) ==H/W== - learn about Error class in nodeJS.
19)  Create all models of DB and create all model files using CLI.
20) search and know more about Schema in this below code & also research about mongoose.model(). ==(Doubt)==
     `import mongoose, { Schema } from "mongoose";`
21)  ==Identify the DT of a variable and put value accordingly==.
     ![[Pasted image 20250404135755.png]]
     Here, enum is one of a key and by nature enum is a type of array that's why we are giving AvailableUserRoles(holding array value) instead of UserRolesEnum(holding an object)
22)  way to store a file in DB
     ![[Pasted image 20250404141955.png]]
     Here, we are taking array type for storing multiple files using obj type if requires otherwise an empty object with array if no file is needed in a task.
     We should ==always store files inside a file storage service== bcoz, if we will put into our DB then DB will take more space and then the bill will be much higher.

23) We can write and send custom error messsage like this,
             `required: [true,"project name is required"]`
     ==H/W : Read about this required field in mongoose==

24) DB schema for storing avatar of an user
     ![[Pasted image 20250404144526.png]]
     here we are taking an ==algo for storing an avatar image like==,
         Opt_1 - first take it from user and then store into our DB then upload it to a file storage service so, in can if file storage service fails then we have a backup opt in our DB.
         Opt_2 - take url from file storage directly don't use DB's localPath.
         But both of these ==two options depends on software's sensitivity==.
         ==taking localPath inside default if in any case placeholder url fails.==

25) Using Mongoose other than just normal properties like name, email, password etc. we can also add functionality to a DB's schema using `SchemaName.methods` which returns an object
     ex - ![[Pasted image 20250406000526.png]]
     We should wrote these methods inside the respective schema ==bcoz it becomes easy to access properties using this keyword== and then can use it later in controllers like in auth controller.
     
26) Using this ==`crypto.createHash("sha256").update(unHashedToken).digest("hex");`== we can hashed the crypto token.
     but how?
         ![[Pasted image 20250406010658.png]]
         ![[Pasted image 20250406010733.png]]
         ![[Pasted image 20250406010919.png]]

     Somtimes we need to do the hashing of mail, password etc. ==due to compliances==.

27) ==HealthCheck controller== - It is used to check the server that either it is up or not. Usually tells to system like AWS that our one sys is down so now up the another one. This could be possible to happen bcoz, AWS have services like which continuously hits to a route after every min/3min  & expects that we will send data to it. so, for this we can't hit any random route like user or etc thats why we need to make a special route for it i.e. healthcheck (as per industry standard).

**Continues... at 30th March also**

28. Port no ==27017== is the default port number used by MongoDB for client-to-server communication.
29. During creating any project we need to install the DB based on our requirement and it could be like mongoDB/postgres or mySQL some times but this is not a easy task that we can do every time due to, configuaration and all things.
     So, for the solution we can use ==DOCKER== that gives us fully configured box of the required DB(mongodb/postgres/Mysql) & that box will run on certain port no.
     ![[Pasted image 20250408153521.png]]
     So for this firstly ==install docker== then ==go to hub.Docker.com== which ==gives== that ==configured box== with all available versions and for using this Docker should be run in background all the time.
     




### Extra & IMP
1. ![[Pasted image 20250406175422.png]]

2. 