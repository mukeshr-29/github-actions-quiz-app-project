FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Create the production image
FROM node:18 AS production
WORKDIR /app
COPY --from=build /app /app
EXPOSE 8080
CMD ["npm", "run" "start"]