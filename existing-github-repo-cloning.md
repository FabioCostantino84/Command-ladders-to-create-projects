# Clonazione repo Github esistente. - Existing Github repo cloning.

## Comando per clonare la repo. 'git clone LINK_CLONAZIONE_COPIATO NOME_DIRECTORY_DI_DESTINAZIONE'. - Command to clone the repo. 'git clone LINK_CLONAZIONE_COPIATO NOME_DIRECTORY_DI_DESTINAZIONE'.
```bash
git clone
```

## Rimozione cartella vecchia .git. -  Removal of the old .git folder.
```bash
rm -rf .git
```

## Inizializzazione, add e commit. - Initialization, add, and commit.
```bash
git init
git add .
git commit -m"initial commit"
```

## 3 Comandi di inizializzazione della repo da copiare da Github, che permette di aggiungere l'origine remota e pushare su Main. - 3 Repo initialization commands to copy from Github, which allows you to add the remote source and push to Main.
```bash
git remote add origin https://github.com/vgianluca96/nome-repo.git
git branch -M main
git push -u origin main
```

## Installazione dipendenze. - Dependency installation.
```bash
composer install
```

## Copia e incolla `.env-example` rinomina in `.env` e modifica (dati del database, nome app, disk su `public`). - Copy and paste `.env-example` rename to `.env` and edit (database data, app name, disk to `public`).

## Generazione chiave. - Key generation.
```bash
php artisan key:generate
```

## Comando storage link. Crea un link simbolico tra il percorso di archiviazione (storage) e il percorso pubblico (public). - Storage link command. Creates a symbolic link between the (storage) location and the (public) location. 
```bash
php artisan storage:link
```

## Se necessario creiamo la cartella di salvataggio in `storage/app/public/nome_cartella`. - If necessary, create the save folder in `storage/app/public/name_folder`.

## Installazione pacchetti npm. - Install npm packages.
```bash
npm install
```

## Migrazione vecchie tabelle. - Migration of old tables.
```bash
php artisan migrate
```

## Seedare le vecchie tabelle. - Seeder the old tables.
```bash
php artisan db:seed
```

## Seedare una singola tabella. - Seeder a single table..
```bash
php artisan db:seed --class=
```