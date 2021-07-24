# rest-api-sucrase

### About
> I decided to develop this project to improve my knowledge with sucrase and MariaDB.

### Come on...
Change the file `.env_example` for `.env`, don't forget to add a secret key.

```
TOKEN_SECRET=secret_key_here
```

Execute the commands below:

```
npm i
npx sequelize db:migrate
npx sequelize db:seed:all
npm run dev
```

At this point your API should be running at the address http://localhost:3001

The default configuration is MySQL/MariaDB, if you want to change it, edit the database in the file `.env`, also configure the `src/config/database.js`.

MySQL/MariaDB settings (default):

```javascript
require('dotenv').config();

module.exports = {
  host: process.env.DATABASE_HOST,
  port: process.env.DATABASE_PORT,
  username: process.env.DATABASE_USERNAME,
  password: process.env.DATABASE_PASSWORD,
  database: process.env.DATABASE,
  dialectOptions: {
    timezone: 'America/Sao_Paulo',
  },
  timezone: 'America/Sao_Paulo',

  define: {
    timestamps: true,
    underscored: true,
    underscoredAll: true,
    createdAt: 'created_at',
    updatedAt: 'updated_at',
  },
};
```

SQLite settings:

```javascript
require('dotenv').config();

module.exports = {
  dialect: 'sqlite',
  storage: './db.sqlite',
  define: {
    timestamps: true,
    underscored: true,
    underscoredAll: true,
    createdAt: 'created_at',
    updatedAt: 'updated_at',
  },
};
```

Note that the settings starting with `process.env.` comes from the file `.env`.

You can get JWT token on route `/tokens`, passing the JSON:

```json
{
	"email": "admin@email.com",
	"password": "123456"
}
```
