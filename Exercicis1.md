## Base de dades edx – col·lecció students

1. Busca els estudiants de gènere masculí
   ```js
   db.students.find({gender:"H"})
   ```
2. Digues quina és la quantitat d’estudiants de gènere femení.
   ```js
   db.students.find({gender:"M"}).count()
   ```
3. Busca els estudiants nascuts l’any 1993
   ```js
   db.students.find({birth_year:1993})
   ```
4. Busca els estudiants de gènere masculí i nascuts l’any 1993
   ```js
   db.students.find({$and:[{birth_year:1993},{gender:"H"}]})
   ```
5. Busca els estudiants nascuts després de l’any 1990
   ```js
   db.students.find({birth_year:{$gt:1990}})
   ```
6. Busca els estudiants nascuts abans o durant l’any 1990
   ```js
   db.students.find({birth_year:{$gte:1990}})
   ```
7. Busca els estudiants nascuts a la dècada dels 90s
   ```js
   db.students.find({birth_year:{$gte:1990, $lte:1999}})
   ```
8.  Busca els estudiants de gènere femani nascus a la dècada dels 90s
    ```js
    db.students.find({$and:[{birth_year:{$gte:1990, $lte:1999}},{gender:"M"}]})
    ```
9.  Busca els estudiants que no han nascut a l’any 1985
    ```js
    db.students.find({birth_year:{$ne:1985}})
    ```
10. Busca aquells estudiants que han nascut l’any 1970,1980 o 1990
    ```js
    db.students.find({birth_year:{$in:[1970,1980,1990]}})
    ```
11. Busca aquells estudiants que no han nascut l’any 1970,1980 o 1990
    ```js
    db.students.find({birth_year:{$nin:[1970,1980,1990]}})
    ```
12. Busca aquells estudiants nascuts en any parell.
    ```js
    b.students.find({birth_year:{$mod:[2,0]}})
    ```
13. Busca els estudiants que tinguin telèfon auxiliar
    ```js
    db.students.find({phone_aux:{$exists:true}})
    ```
14. Busca els estudiants que no tinguin telèfon auxiliar
    ```js
    db.students.find({phone_aux:{$exists:false}})
    ```
15. Busca els estudiants que no tinguin segon cognom
    ```js
    db.students.find({lastname2:{$exists:false}})
    ```
16. Busca els estudiants que tinguin telèfon auxiliar i només el primer cognom
    ```js
    db.students.find({$and:[{lastname2:{$exists:false}},{phone_aux:{$exists:true}}]})
    ```
17. Busca els estudiants que el seu correu electrònic acabi en .net
    ```js
    db.students.find({email:/.net$/})
    ```
18. Busca els estudiants que el seu telèfon comenci per 622
    ```js
    db.students.find({phone:/^622/})
    ```
19. Busca els estudiants que el seu dni comenci i acabi amb una lletra
    ```js
    
    ```
20. Busca els estudiants que el seu nom comenci per una vocal
    ```js
    db.students.find({name:/^[AEIOU]/})
    ```
21. Busca els estudiants que el seu nom sigui compost
    ```js
    db.students.find({name:/\s/})
    ```
22. Busca els estudiants amb un nom més llarg de 13 caràcters
    ```js
    db.students.find({$expr:{$gt:[{$strLenCP:"$name"},13]}})
    ```
23. Busca els estudiants amb 3 o més vocals en el seu nom
    ```js
    db.students.find({name:/[AEIOUaeiou]{3}/})
    ```


## Base de dades edx – col·lecció bios

24. Busca aquells desenvolupadors que han realitzat contribucions en OOP
    ```js
    db.bios.find({contribs:{$in:["OOP"]}})
    ```
25. Busca aquells desenvolupadors que han realitzat contribucions en OOP o Java
    ```js
    db.bios.find({contribs:{$in:["OOP","Java"]}})
    ```
26. Busca aquells desenvolupadors que han realitzat contribucions en OOP i Simula
    ```js
    db.bios.find({contribs:{$all:["OOP","Simula"]}})
    ```
27. Busca aquells desenvolupadors que siguin vius
    ```js
    db.bios.find({deathYear:{$exists:false}})
    ```
28. Busca aquells desenvolupadors que siguin morts
    ```js
    db.bios.find({deathYear:{$exists:true}})
    ```
29. Busca aquells desenvolupadors que han obtingut un premi a l’any 2002
    ```js
    db.bios.find({awards:{$elemMatch:{"year":{$eq:2002}}}})
    ```
30. Busca aquells desenvolupadors que han obtingut exactament 3 premis.
    ```js
    db.bios.find({awards:{$size:3}})
    ```

