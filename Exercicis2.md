## Exercicis $group
1. Mostra la quantitat d’empleats per cada departament. Mostra id de departament i la quantitat.
   ```js
   db.empleats.aggregate([{$group:{_id:"$departament.codi",quantitatEmpleats:{$count:{}}}}])
   ```
2. Si no ho has tingut en compte en l’exercici anterior. Només tingues en compte aquells empleats que estiguin en un departament.
   ```js
   db.empleats.aggregate([{$match:{"departament":{$exists:true}}},{$group:{_id:"$departament.codi",quantitatEmpleats:{$count:{}}}}])
   ```
3. Ordena el resultat anterior per els departament de més a menys nombre d’empleats.
   ```js
   db.empleats.aggregate([{$match:{"departament":{$exists:true}}},{$group:{_id:"$departament.codi",quantitatEmpleats:{$count:{}}}},{$sort:{quantitatEmpleats:-1}}])
   ```
4. De cada departament mostra el salari més alt. Mostra id de departament i el salari més alt.
   ```js
   db.empleats.aggregate([{$match:{"departament":{$exists:true}}},{$group:{_id:"$departament.codi",quantitatEmpleats:{$count:{}},salariMaxim:{$max:"$salari"}}}])
   ```
5. Quina és la massa salarial de cada departament? Mostra id de departament i la massa salarial.
   ```js
   db.empleats.aggregate([{$match:{"departament":{$exists:true}}},{$group:{_id:"$departament.codi",quantitatEmpleats:{$count:{}},massaSalarial:{$sum:"$salari"}}}])
   ```
6. Només mostra aquells departaments que tinguin una massa salarial igual o superior a 19000
   ```js
   db.empleats.aggregate([{$group:{_id:"$departament.codi",quantitatEmpleats:{$count:{}},massaSalarial:{$sum:"$salari"}}},{$match:{"massaSalarial":{$gte:19000}}}])
   ```