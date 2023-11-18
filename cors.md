# CORS (cross origin resource sharing)

## In `config/cors.php`
- In questo modo `*` tutte le origini possono consumare i dati. - This way '*' all sources can consume the data.
```php
'allowed_origins' => ['*'],
```

- Possiamo inserire direttamente nell'array l'url o aggiungere nel file `.env` una variabile. - We can insert the url directly into the array or add a variable to the `.env` file.
```bash
APP_FRONTEND_URL=http://localhost:5174
```

- Possiamo inserirla nel valore della chiave. - We can put it in the value of the key.
```php
'allowed_origins' => ['APP_FRONTEND_URL', 'http://localhost:5174'], // IL SECONDO E' UN VALORE DI DEFAULT
```

