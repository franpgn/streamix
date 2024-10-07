# **Streamix - Movie Streaming CMS**

Streamix is a Content Management System (CMS) for managing movie data, similar to a platform like Netflix. This Appsmith-based app allows users to upload, view, search, filter, edit, and delist movies stored in a PostgreSQL database.

## **Features**
- **CSV/JSON Upload**: Add movie data by uploading CSV or JSON files.
- **Inline Editing**: Modify movie details directly in the table view.
- **Detailed Movie View**: Edit all fields for individual movies in a detailed view.
- **Search & Filters**: Search movies by name, and filter by genre, rating, and other fields.
- **Delist Movies**: Mark movies as "delisted" when their distribution license expires.

## **Live Application**
You can access the app [here](https://app.appsmith.com/app/streamix/movies-66ff5b88762fac387e09bdb7?branch=main).

---

## **Getting Started**

Follow these instructions to set up and run the Streamix app locally, with access to the PostgreSQL database using Ngrok.

### **Prerequisites**
1. [Docker](https://docs.docker.com/get-docker/)
2. [Docker Compose](https://docs.docker.com/compose/install/)
3. [Ngrok](https://ngrok.com/)
4. [Appsmith Community Edition](https://docs.appsmith.com/getting-started/setup/installation-guides)

### **1. Clone the Repository**

```bash
git clone https://github.com/yourusername/streamix-cms.git
cd streamix-cms
```

### **2. Set Up PostgreSQL Database with Docker Compose**
```bash
docker-compose up -d
```
```yaml
version: '3'
services:
  db:
    image: postgres:13
    container_name: streamix_postgres
    environment:
      POSTGRES_DB: streamix
      POSTGRES_USER: app_user
      POSTGRES_PASSWORD: app_password
    ports:
      - "5432:5432"
    volumes:
      - ./pgdata:/var/lib/postgresql/data
```
### **3. Expose PostgreSQL Using Ngrok**
To make your local PostgreSQL database accessible to Appsmith, you need to expose it using Ngrok.

1.Start Ngrok to expose port 5432 (PostgreSQL default port):
```bash
ngrok tcp 5432
```
2.Ngrok will provide a forwarding address that looks like this: tcp://0.tcp.ngrok.io:XXXXX. Copy this URL.

### **4. Configure Appsmith to Connect to the Database**
In your Appsmith app, configure the PostgreSQL connection settings:
Host: 0.tcp.ngrok.io
Port: XXXXX (provided by Ngrok
Database Name: streamix
Username: app_user
Password: app_password

### **5. Load Sample Data**
Once the PostgreSQL database is running and exposed via Ngrok, you can use the Upload Movies page in the app to populate the database with movie data.

Navigate to the Upload Movies page in Streamix.
Upload a CSV/JSON dataset to add movies.
Alternatively, you can manually import the data using SQL or a database GUI tool (like pgAdmin).

### **6. Running the App**
Access the app through the provided Appsmith link or your local Appsmith instance.
Ensure the app is connected to the PostgreSQL database via Ngrok.
Start managing movie data—add, view, edit, filter, and delist movies.


![](https://raw.githubusercontent.com/appsmithorg/appsmith/release/static/appsmith_logo_primary.png)

This app is built using Appsmith. Turn any datasource into an internal app in minutes. Appsmith lets you drag-and-drop components to build dashboards, write logic with JavaScript objects and connect to any API, database or GraphQL source.

![](https://raw.githubusercontent.com/appsmithorg/appsmith/release/static/images/integrations.png)

### [Github](https://github.com/appsmithorg/appsmith) • [Docs](https://docs.appsmith.com/?utm_source=github&utm_medium=social&utm_content=appsmith_docs&utm_campaign=null&utm_term=appsmith_docs) • [Community](https://community.appsmith.com/) • [Tutorials](https://github.com/appsmithorg/appsmith/tree/update/readme#tutorials) • [Youtube](https://www.youtube.com/appsmith) • [Discord](https://discord.gg/rBTTVJp)

##### You can visit the application using the below link

###### [![](https://assets.appsmith.com/git-sync/Buttons.svg) ](https://app.appsmith.com/applications/66ff5b88762fac387e09bdb3/pages/66ff5b88762fac387e09bdb7) [![](https://assets.appsmith.com/git-sync/Buttons2.svg)](https://app.appsmith.com/applications/66ff5b88762fac387e09bdb3/pages/66ff5b88762fac387e09bdb7/edit)
