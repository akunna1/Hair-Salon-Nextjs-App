## Bantu African Hair Braiding Salon Nextjs-App
### Definitions
- ShadCN: a UI component library for building accessible, customizable, and reusable components in React applications e.g buttons, dropdown menus etc, designed to improve development efficiency and user experience. Almost like BootStrap

### Project Layout (directories)
- Public/images
- src/app --> global.css, favicon.ico, layout.tsx (root layout), page.tsx (first page?)
- src/app/(salon) --> layout.tsx, template.tsx
- src/app/(salon)/booking --> page.tsx
- src/app/(salon)/users --> page.tsx
- src/app/api/auth/[KindeAuth] --> route.tsx
- src/app/login --> page.tsx
- src/components --> Header.tsx, theme-provider.tsx, NavButton.tsx, ModeToggle.tsx
- src/components/ui --> button.tsx (created by shadcn), dropdown-menu.tsx (created by shadcn)
- src/lib --> utlis.js (created by shadcn)

### Features/ Progress of App
- Replace current note book system
- Add a public facing page with basic contact info ✅
 - Add a passwordless employee login to the app
 - Show a real-time open tickets page after login
 - Provide easy navigation & search for customers & tickets
 - Provide a logout option
 - Require users to login at least once per week (did that by changng SSO session inactivity timeout on Kinde to 604800 second)✅
 - Provide a way to remove employee access asap if needed
 - Customers have an ID, full address, phone, email & notes
 - Tickets have an ID, title, notes, created & updated dates
 - Tickets are either OPEN or COMPLETED
 - Tickets are assigned to specific employees
 - Users can have Employee, Manager, or Admin permissions
 - All users can create and view tickets
 - All users can create, edit and view customers
 - Employees can only edit their assigned tickets
 - Managers and Admins can view, edit, and delete all tickets
 - Desktop mode is most important but the app should be usable on tablet and phone devices as well
 - Light / Dark mode option requested by employees ✅

### Useful links
- https://ui.shadcn.com/docs/dark-mode/next
- https://lucide.dev/icons/
  
### Key Differences between next.js app and a vite-react.js app
- paths in vite-react.js are defined in index.jsx. However, paths in next.js are defined under app by creating a () folder under it, which have other folders that have a page.tsx page in them. There's no index.jsx file in next.js
- app title and favicon are defined in index.html in a vite-react.js project. However, in next.js, the app titles are different in page.tsx of the router folders. 
