# Relazione many-to-many - Many-to-many relationship

## Creazione di una relazione many-to-many tra due modelli: `Student` e `Course`. Uno studente può essere iscritto a molti corsi, e un corso può avere molti studenti. - Creating a many-to-many relationship between two models: `Student` and `Course`. A student can be enrolled in many courses, and a course can have many students.

### Creare Modelli e Migrazioni - Create templates and migrations

- Questi comandi creano i modelli Student e Course insieme alle rispettive migrazioni. - These commands create the Student and Course templates along with their migrations.
```bash
php artisan make:model Student -ms
```
```bash
php artisan make:model Course -ms
```

### Eseguire le Migrazioni - Perform Migrations

- Questo comando esegue le migrazioni, creando le tabelle students e courses nel database. - This command performs migrations, creating the students and courses tables in the database.

```bash
php artisan migrate
```

### Creare la Migrazione della Tabella Pivot - Creating the PivotTable Migration

```bash
php artisan make:migration create_course_student_table
```
### Modificare la migrazione appena per definire la struttura della tabella Pivot - Modify the migration just to define the structure of the PivotTable

```php
// Migrazione Tabella Pivot - PivotTable Migration
public function up()
{
    Schema::create('course_student', function (Blueprint $table) {
        $table->id();
        $table->unsignedBigInteger('course_id');
        $table->unsignedBigInteger('student_id');
        $table->timestamps();

        $table->foreign('course_id')->references('id')->on('courses')->onDelete('cascade');
        $table->foreign('student_id')->references('id')->on('students')->onDelete('cascade');
    });
}
```

### Eseguire le Migrazioni - Perform Migrations

- Questo comando esegue la migrazione per la tabella intermedia, creando la tabella `course_student` nel database. - This command migrates to the intermediate table, creating the `course_student` table in the database.

```bash
php artisan migrate
```

### Definiamo la Relazione nei Modelli - Defining the Relationship in the Models

- Nei modelli `Student` e `Course`, definisci la relazione many-to-many utilizzando il metodo `belongsToMany`. - In the `Student` and `Course` models, define the many-to-many relationship using the `belongsToMany` method.

```php
// Nel modello Student - In the Student model
public function courses()
{
    return $this->belongsToMany(Course::class);
}

// Nel modello Course - In the Course model
public function students()
{
    return $this->belongsToMany(Student::class);
}
```

### Esempio di Utilizzo - Example of Use

```php
// Creare un nuovo studente e assegnargli alcuni corsi - Create a new student and assign some courses to them
$student = Student::create(['name' => 'John Doe']);
$student->courses()->attach([1, 2, 3]); // Supponiamo che 1, 2, 3 siano ID di corsi esistenti - Assume that 1, 2, 3 are existing course IDs

// Ottenere i corsi a cui è iscritto uno studente - Get the courses that a student is enrolled in
$courses = $student->courses;

// Ottenere gli studenti iscritti a un corso - Get the students enrolled in a course
$course = Course::find(1); // Supponiamo che 1 sia l'ID di un corso esistente - Assume that 1 is an existing course ID
$students = $course->students;
```
