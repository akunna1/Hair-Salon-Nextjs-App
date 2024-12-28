## Bantu African Hair Braiding Salon Nextjs-App
### Definitions
- ShadCN: a UI component library for building accessible, customizable, and reusable components in React applications e.g buttons, dropdown menus etc, designed to improve development efficiency and user experience. Almost like BootStrap
- Middleware: a function or a set of functions that intercept and process requests and responses in an application before they reach their intended destination or are sent back to the client. It acts as a "middle layer" between the incoming HTTP request and the final application logic.
- Neon HTTP adapter: used to enable seamless integration between Drizzle ORM and Neon’s serverless database, providing a lightweight and efficient way to interact with the database over HTTP.
  
### Project Layout (directories)
- Public/images
- src/app --> global.css, favicon.ico, layout.tsx (root layout, favicon defined here, themeProvider and footer are called here), page.tsx (first page?)
- src/app/(salon) --> layout.tsx, template.tsx
- src/app/(salon)/booking --> page.tsx
- src/app/(salon)/booking/form --> page.tsx
- src/app/(salon)/users --> page.tsx
- src/app/(salon)/tickets --> page.tsx (protected route)
- src/app/(salon)/tickets/form --> page.tsx, customerForm.tsx
- src/app/api/auth/[KindeAuth] --> route.tsx
- src/components --> Header.tsx (logo and icons are called here), Header2.tsx, Footer.tsx, theme-provider.tsx, NavButton.tsx, ModeToggle.tsx
- src/components/ui --> button.tsx (created by shadcn), dropdown-menu.tsx (created by shadcn), form.tsx, label.tsx, checkbox.tsx, textarea.tsx, etc
- src/components/inputs --> inputWithLabel.tsx
- src/constants --> statesArray.tsx 
- src/lib/queries --> getCustomer.ts, getTicket.ts
- src/lib --> utlis.ts (created by shadcn)
- src --> middleware.ts (handles authentication)
- src/db --> index.ts, schema.ts, migrate.ts
- src/zod-schemas --> customers.ts, tickets.ts
- salon-app (main folder) --> drizzle.config.ts, .env.local, package.json
- salon-app/ data  --> customers.sql (contains sql statement to insert some data), tickets.sql

### Features/ Progress of App
Completion rate = 11/21 = 52.4%
  ____________________________________________________________________________________________________________________________________________________________________________
1.  Replace current note book system 
2. Add a public facing page with basic contact info ✅
3. Add a passwordless employee login to the app ✅
4. Show a real-time open tickets page after login
5. Provide easy navigation & search for customers & tickets
6. Provide a logout option ✅
7. Require users to login at least once per week (did that by changng SSO session inactivity timeout on Kinde to 604800 second)✅
8. Provide a way to remove employee access asap if needed (Users can be deleted/ suspended in Kinde) ✅
9. Customers have an ID, full address, phone, email & notes ✅
10. Tickets have an ID, title, notes, created & updated dates ✅
11. Tickets are either OPEN or COMPLETED ✅
12. Tickets are assigned to specific employees ✅
13. Users can have Employee, Manager, or Admin permissions 
14. All users can create and view tickets ✅
15. All users can create, edit and view customers ✅
16. Employees can only edit their assigned tickets
17. Managers and Admins can view, edit, and delete all tickets
18. Desktop mode is most important but the app should be usable on tablet and phone devices as well (make app completely mobile responsive)
19. Light / Dark mode option requested by employees (make it work on all pages)
20. 'Lock' necessary pages
21. Put headers on all pages except the homepage

### Useful links
- https://ui.shadcn.com/docs/dark-mode/next
- https://lucide.dev/icons/
- https://console.neon.tech/app/projects
- https://neon.tech/docs/get-started-with-neon/connect-neon

### Useful commands
- npm i drizzle-orm @neondatabase/serverless
- npm i -D drizzle-kit tsx dotenv
  
### Key Differences between next.js app and a vite-react.js app
- paths in vite-react.js are defined in index.jsx. However, paths in next.js are defined under app by creating a () folder under it, which have other folders that have a page.tsx page in them. There's no index.jsx file in next.js
- app title and favicon are defined in index.html in a vite-react.js project. However, in next.js, the app titles are different in page.tsx of the router folders, and favicons are defined in the root layout.tsx file (so is the footer).

### Using Kinde
- helps with passwordless auth
- create account --> type in business details (has kinde domain) --> use existing code base (next.js project) --> do the npm stuff --> update .env.local (found in same place as package.json, modify redirect Urls) --> create API endpoint to handle kinde Auth endpoints in the next.js app (src/app/api/auth/[KindeAuth]/route.ts) --> add login button to the users page --> rename application (under details) --> make sure to change the logout redirect url to match that of the .env.local file (under details) --> modify authentication experience (under details) --> email + code enabled (under authrntication) --> modify SSO session inactivity timeout (under tokens) --> go back to home --> go to users and add users e.g me (one can delete/suspend users here) --> go back to home and to settings --> set time zone and add a valid email for the business (i.e my email) --> go to permissions (still under settings) --> add admin and key (i.e admin), do the same for manager and user (they will have authorization to use certain features of the application) --> go to policies (still under settings) --> deactivate 'allow self-sign up' --> go to multi-factor authentication and make it not required --> add a logout link to the header

### Adding Permissions in Kinde
- Home --> user --- three dots ---> view profile --> permissions --> Add permissions --> make me admin and manager --> save -->
- Add one more user: homepage --> User --> add user
- add application called ManagementAPI --> choose M2M --> update .env.local file with credentials
- Select APIs on the menu on the left --> authorize application
- set up scope --> turn on read:users --> 

### Manually Added to package.json under 'scripts'
- "db:generate": "drizzle-kit generate --config drizzle.config.ts",
- "db:migrate": "tsx ./src/db/migrate.ts" (needs connection string from neon)

### Other Used SQL Commands
-- UPDATE Tickets SET request = 'new-ticket@gmail.com' 
- TRUNCATE tickets, customers RESTART IDENTITY CASCADE;

### Testing...
- http://localhost:3000/booking/form?customerId=2
- http://localhost:3000/tickets/form?ticketId=24

### Installations
- npm i @kinde-oss/kinde-auth-nextjs @kinde/management-api-js
