<h1>Gestion des Patients - Spring MVC</h1>

<h3>Projet réalisé par Zineb Feth-Eddine</h3>

---

<h2>Introduction</h2>
<p>
Ce projet consiste à développer une application web basée sur <strong>Spring MVC</strong>, <strong>Thymeleaf</strong>, et <strong>Spring Data JPA</strong> pour la gestion des patients.
</p>
<ul>
    <li>Afficher la liste des patients avec pagination.</li>
    <li>Rechercher des patients par mot-clé.</li>
    <li>Ajouter un nouveau patient.</li>
    <li>Modifier les informations d'un patient.</li>
    <li>Supprimer un patient.</li>
</ul>
<p>
Initialement, une base de données <strong>H2</strong> en mémoire était utilisée pour simplifier le développement. Cependant, pour une utilisation pratique et persistante, nous avons migré vers une base de données <strong>MySQL</strong>.
</p>

---

<h2>Structure du Projet</h2>
<p>Le projet suit une architecture bien structurée respectant le paradigme <strong>MVC (Modèle-Vue-Contrôleur)</strong>.</p>
<img src="/TP3-Patients-mvc - part2/Screens/str.png" alt="Structure" />

<h3>1. Package <code>entities</code></h3>
<ul>
    <li>Contient la classe <strong>Patient</strong>, représentant le modèle de données de l'application.</li>
    <li><strong>Attributs</strong> :
        <ul>
            <li><code>id</code> : Identifiant unique.</li>
            <li><code>nom</code> : Nom du patient.</li>
            <li><code>dateNaissance</code> : Date de naissance.</li>
            <li><code>score</code> : Score attribué au patient.</li>
            <li><code>malade</code> : Statut booléen indiquant si le patient est malade ou non.</li>
        </ul>
    </li>
</ul>

<h3>2. Package <code>repositories</code></h3>
<ul>
    <li>Contient l'interface <strong>PatientRepository</strong>, héritant de <code>JpaRepository</code>.</li>
    <li>Fournit les opérations CRUD automatiques et une méthode personnalisée pour la recherche (<code>findByNameContaining</code>).</li>
</ul>

<h3>3. Package <code>web</code></h3>
<ul>
    <li>Contient le contrôleur <strong>PatientController</strong>.</li>
    <li><strong>Responsabilités</strong> :
        <ul>
            <li>Gérer la logique métier et les données.</li>
            <li>Naviguer entre les différentes pages (patients, formulaire d'ajout/modification).</li>
            <li>Transmettre les données au modèle Thymeleaf.</li>
        </ul>
    </li>
</ul>

<h3>4. Dossier <code>resources/templates</code></h3>
<ul>
    <li>Contient les fichiers <strong>Thymeleaf</strong> pour l'interface utilisateur :</li>
    <ul>
        <li><code>patients.html</code> : Liste des patients avec pagination et recherche.</li>
        <li><code>formPatients.html</code> : Formulaire d'ajout d'un nouveau patient.</li>
        <li><code>editPatient.html</code> : Formulaire de modification des informations d'un patient.</li>
        <li><code>template1.html</code> : Structure commune pour les pages.</li>
    </ul>
</ul>

<h3>5. Dossier <code>resources/static</code></h3>
<ul>
    <li>Conçu pour les fichiers statiques comme CSS ou JS. Actuellement, non utilisé dans ce projet.</li>
</ul>

<h3>6. Fichier <code>application.properties</code></h3>
<ul>
    <li>Configuration de la base de données MySQL :</li>
</ul>

<pre>
spring.datasource.url=jdbc:mysql://localhost:3306/PAT_DB?createDatabaseIfNotExist=true
spring.datasource.username=root
spring.datasource.password=
spring.jpa.hibernate.ddl-auto=update
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MariaDBDialect
</pre>

---

<h2>Description des Fonctionnalités</h2>

<h3>1. Liste des Patients (<code>patients.html</code>)</h3>
<p>
Affiche un tableau paginé avec une barre de recherche.
Actions possibles :
</p>
<ul>
    <li>Ajouter un patient.</li>
    <li>Modifier les informations d'un patient.</li>
    <li>Supprimer un patient.</li>
</ul>
<p><strong>Exemple de capture d'écran :</strong></p>
<img src="/TP3-Patients-mvc - part2/Screens/1.png" alt="Liste des Patients" />

<h3>2. Formulaire d'Ajout d'un Patient (<code>formPatients.html</code>)</h3>
<p>
Permet d'enregistrer un nouveau patient en remplissant un formulaire.
Inclut des validations pour s'assurer que les données saisies sont valides.
</p>
<p><strong>Exemple de capture d'écran :</strong></p>
<img src="/TP3-Patients-mvc - part2/Screens/3.png" alt="Ajout d'un Patient" />
<img src="/TP3-Patients-mvc - part2/Screens/4.png" alt="Ajout d'un Patient" />


<h3>3. Formulaire de Modification (<code>editPatient.html</code>)</h3>
<p>
Permet de modifier les informations d’un patient existant.
</p>
<p><strong>Exemple de capture d'écran :</strong></p>
<img src="/TP3-Patients-mvc - part2/Screens/8.png" alt="Modification d'un Patient" />
<img src="/TP3-Patients-mvc - part2/Screens/9.png" alt="Modification d'un Patient" />

<h3>Suppression d'un Patient</h3>
<p>
La fonctionnalité de suppression permet d'effacer un patient directement depuis la liste affichée dans <code>patients.html</code>. 
Un bouton "Delete" est disponible pour chaque ligne du tableau, et l'action est effectuée après confirmation.
</p>
<p><strong>Exemple de capture d'écran :</strong></p>
<img src="/TP3-Patients-mvc - part2/Screens/6.png" alt="Suppression d'un Patient" />


---

<h2>Conclusion</h2>
<p>
Le projet illustre comment développer une application web robuste et évolutive avec <strong>Spring MVC</strong>, <strong>Thymeleaf</strong>, et une base de données <strong>MySQL</strong>. Cette application peut être étendue pour inclure des fonctionnalités supplémentaires telles que la gestion des utilisateurs et l'exportation des données.
</p>
