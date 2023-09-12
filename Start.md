## Todo List setup

download node.js

Visual Studio Code
```text
ES7+ React/Redux/React-Native snippets
JavaScript and TypeScript Nightly
Tailwind CSS IntelliSense
```
### Install Next.js
```text
npx create-next-app@latest .

	What is your project named? to-do-list
	Would you like to use TypeScript?  Yes
	Would you like to use ESLint?  Yes
	Would you like to use Tailwind CSS?  Yes
	Would you like to use `src/` directory? Yes
	Would you like to use App Router? (recommended) Yes
	Would you like to customize the default import alias? No
```
--------------------------------------
### prisma database
```text
npm i prisma --save-dev

npx prisma init --datasource-provider sqlite
```
prisma\schema.prisma  
```javascript
add model ToDo

model ToDo {
	id          String @id @default(uuid())
	title       String
	complete    Boolean
	createdAt   DateTime @default(now())
	updatedAt   DateTime @updatedAt
}
```
Initialize prisma
```text
npx prisma migrate dev --name init
```
src\db.ts
```ts
import { PrismaClient } from "@prisma/client";

const globalForPrisma = global as unknown as {
    prisma: PrismaClient | undefined
}

export const prisma = globalForPrisma.prisma ?? new PrismaClient({log: ['query']},)

if (process.env.NODE_ENV !== 'production') globalForPrisma.prisma = prisma
```
-----------------------------------------

npm run dev

http://localhost:3000/
