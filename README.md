
 1. Clone the Repository

> Or use your existing app folder.

---

 2. Create the Dockerfile

dockerfile
FROM node:16

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "app.js"]


 3. Build the Docker Image


docker build -t week05_1:1 .

 4. Create Docker Compose File

`docker-compose.yml`:

yaml
version: '3'
services:
  web:
    image: week05_1:1
    build: .
    ports:
      - "3000:3000"


 5. Start the App Using Docker Compose


docker-compose up


Visit the app: [http://localhost:3000](http://localhost:3000)

 6. Push Docker Image to Docker Hub

 a. Login to Docker Hub


docker login


 b. Tag the image


docker tag week05_1:1 s223986848/week05_1:1


 c. Push the image


docker push s223986848/week05_1:1


---

 Testing the App

Use browser or `curl`:


curl http://localhost:3000

