## Bantu African Hair Braiding Salon Nextjs-App
### Definitions
- ShadCN: a UI component library for building accessible, customizable, and reusable components in React applications, designed to improve development efficiency and user experience. Almost like BootStrap

### Project Layout (directories)
- Public/images
- src/app --> global.css, favicon.ico, layout.tsx (root layout), page.tsx (first page?)
- src/app/(salon) --> layout.tsx, template.tsx
- src/app/(salon)/tickets --> page.tsx
- src/app/(salon)/customers --> page.tsx
- src/app/(salon)/home --> page.tsx
- src/components --> Header.tsx
- src/components --> theme-provider.tsx
- src/components --> NavButton.tsx
- src/components --> ModeToggle.tsx
- src/components/ui --> button.tsx (created by shadcn)
- src/components/ui --> dropdown-menu.tsx (created by shadcn)
- src/lib --> utlis.js (created by shadcn)

### Features of App
- Replace current note book system
- Add a public facing page with basic contact info
 - Add a passwordless employee login to the app
 - Show a real-time open tickets page after login
 - Provide easy navigation & search for customers & tickets
 - Provide a logout option
 - Require users to login at least once per week
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
 - Light / Dark mode option requested by employees
 - Expects quick support if anything goes wrong with the app

### Useful links
- https://ui.shadcn.com/docs/dark-mode/next
- https://lucide.dev/icons/
  
### Key Differences between next.js app and a vite-react.js app
- paths in vite-react.js are defined in index.jsx. However, paths in next.js are defined under app by creating a () folder under it, which have other folders that have a page.tsx page in them. There's no index.jsx file in next.js
- app title and favicon are defined in index.html in a vite-react.js project. However, in next.js...
