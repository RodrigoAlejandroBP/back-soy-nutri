# API REST Soy Nutri

## Las rutas disponibles en la API, con sus respectivos campos y restricciones, son las siguientes:

### 1. Add user admin

<details>
    <summary>Detalles</summary>
    <dl>
        <dt><li>Url: https://us-central1-back-f0378.cloudfunctions.net/api/adminAuth/signup</li></dt>
        <dt><li>Tipo de petición: POST</li></dt>
        <dt><li>Parámetros</li></dt>
            <dd><li>NA.</li></dd>
        <dt><li>Restricciones</li></dt>
            <dd><li>Solo puede existir un administrador, al ingresarlo se bloquea la creación de otro.</li></dd>
        <dt><li>Campos necesarios</li></dt>
            <dd>
                <li>rut</li>
                <li>password</li>
            </dd>
        <dt><li>Respuesta: estado (status code) y Token</li></dt>
    </dl>
</details>

### 2. Login admin

<details>
    <summary>Detalles</summary>
    <dl>
        <dt><li>Url: https://us-central1-back-f0378.cloudfunctions.net/api/adminAuth/login</li></dt>
        <dt><li>Tipo de petición: POST</li></dt>
        <dt><li>Parámetros</li></dt>
            <dd><li>NA.</li></dd>
        <dt><li>Restricciones</li></dt>
            <dd><li>NA.</li></dd>
        <dt><li>Campos necesarios</li></dt>
            <dd>
                <li>rut</li>
                <li>password</li>
            </dd>
        <dt><li>Respuesta: estado (status code), Token y rut</li></dt>
    </dl>
</details>

### 3. Change admin password

<details>
    <summary>Detalles</summary>
    <dl>
        <dt><li>Url: https://us-central1-back-f0378.cloudfunctions.net/api/adminAuth/changePassword</li></dt>
        <dt><li>Tipo de petición: POST</li></dt>
        <dt><li>Parámetros</li></dt>
            <dd><li>NA.</li></dd>
        <dt><li>Restricciones (Se debe enviar un header con la siguiente información)</li></dt>
            <dd>
                <li>key: Authorization</li>
                <li>value: Bearer + Token inicio de sesión del administrador</li>
            </dd>
        <dt><li>Campos necesarios</li></dt>
        <dd>
            <li>rut</li>
            <li>password</li>
            <li>newPassword</li>
        </dd>
        <dt><li>Respuesta: estado (status code), Token y mensaje</li></dt>
    </dl>
</details>

### 4. Create patient

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsAuth/signup
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - names
  - father_last_name
  - mother_last_name
  - city
  - email
  - phone
  - birth_date
  - sex
  - alimentation
- Respuesta: estado (status code) y Token

### 5. Login patient

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsAuth/login
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - NA.
- Campos necesarios:
  - rut
  - password
- Respuesta:
  - Token
  - rut
  - names
  - father_last_name
  - mother_last_name
  - city
  - email
  - phone
  - birth_date
  - sex
  - alimentation
  - in_date
  - state

### 6. Change patient password

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsAuth/changePassword
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del paciente
- Campos necesarios:
  - rut
  - password
  - newPassword
- Respuesta: estado (status code), Token y mensaje

### 7. Add control to patient

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/addControl
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
  - weight
  - size
  - cbr
  - cbc
  - cc_min
  - cc_max
  - cad_max
  - triceps_fold
  - subscapular_fold
  - abdominal_fold
  - imc
  - dni
  - biological_age
  - visceral_fat
  - fat
  - mass
  - muscle_mass
- Respuesta: estado (status code) y mensaje

### 8. Get Carnet

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/getCarnet/:user/:rut
- Tipo de petición: GET
- Parámetros:
  - user: selección de middleware a utilizar según el tipo de token, admin o patient
  - rut: rut del paciente a obtener el carnet
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador o Paciente
- Campos necesarios:
  - NA.
- Respuesta: estado (status code) y carnet

### 9. Get Control with date

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/getCarnet/:user/:rut/:date
- Tipo de petición: GET
- Parámetros:
  - user: selección de middleware a utilizar según el tipo de token, admin o patient
  - rut: rut del paciente a obtener el carnet
  - date: fecha del control a solicitar
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador o Paciente
- Campos necesarios:
  - NA.
- Respuesta: estado (status code) y Control de la fecha seleccionada

### 10. Modify Control

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/modifyControl
- Tipo de petición: PUT
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
  - weight
  - size
  - cbr
  - cbc
  - cc_min
  - cc_max
  - cad_max
  - triceps_fold
  - subscapular_fold
  - abdominal_fold
  - imc
  - dni
  - biological_age
  - visceral_fat
  - fat
  - mass
  - muscle_mass
- Respuesta: estado (status code) y mensaje

### 11. Delete one control

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/deleteControl
- Tipo de petición: DELETE
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
- Respuesta: estado (status code) y mensaje

### 12. Delete all control

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/deleteCarnet
- Tipo de petición: DELETE
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
- Respuesta: estado (status code) y mensaje

### 13. Add biochemical analysis

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/addBiochemical
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
  - b12
  - d
- Respuesta: estado (status code) y mensaje

### 14. Get biochemical analysis

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/getBiochemical/:user/:rut
- Tipo de petición: GET
- Parámetros:
  - user: selección de middleware a utilizar según el tipo de token, admin o patient
  - rut: rut del paciente a obtener el análisis bioquímico
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador o Paciente
- Campos necesarios:
  - NA.
- Respuesta: estado (status code) y carnet

### 15. Get biochemical analysis with date

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/getBiochemical/:user/:rut/:date
- Tipo de petición: GET
- Parámetros:
  - user: selección de middleware a utilizar según el tipo de token, admin o patient
  - rut: rut del paciente a obtener el análisis bioquímico
  - date: fecha del análisis bioquímico a solicitar
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador o Paciente
- Campos necesarios:
  - NA.
- Respuesta: estado (status code) y Control de la fecha seleccionada

### 16. Modify biochemical analysis

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/modifyBiochemical
- Tipo de petición: PUT
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
  - b12
  - d
- Respuesta: estado (status code) y mensaje

### 17. Delete one biochemical analysis

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/deleteBiochemical
- Tipo de petición: DELETE
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
- Respuesta: estado (status code) y mensaje

### 18. Delete all biochemical analysis

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsCarnet/deleteAllBiochemical
- Tipo de petición: DELETE
- Parámetros:
  - NA.
- Restricciones:
  - Se debe enviar un header con la siguiente información:
    - key: Authorization
    - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
- Respuesta: estado (status code) y mensaje

### 19. Add a daily diet.

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsDailyDiets/addDailyDiet
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - key: Authorization
  - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
  - breakfast_time
  - breakfast
  - lunch_time
  - lunch
  - snack_time
  - snack
  - post_training
  - dinner_time
  - dinner
  - calories
  - proteins
  - goals
  - extra_info
- Respuesta: estado (status code) y mensaje

### 20. Get a daily diet.

### 21. Modify a daily diet.

### 22. Delete a daily diet.


### 23. Add a weekly diet.

- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patientsWeeklyDiets/addWeeklyDiet
- Tipo de petición: POST
- Parámetros:
  - NA.
- Restricciones:
  - key: Authorization
  - value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - rut
  - date
  - day
  - breakfast
  - lunch
  - snack
  - post_training (not mandatory)
  - dinner

- Respuesta: estado (status code).

### 24. Get a weekly diet.


  Url:https://us-central1-back-f0378.cloudfunctions.net/api/patientsWeeklyDiets/getWeeklyDiets
  - Tipo de petición: GET
- Parámetros:
  - NA.
- Restricciones:
  - Key: Authorization
  - Value: Bearer + Token inicio de sesión del administrador o paciente
- Campos necesarios:
  - Rut
  - Date

- Respuesta: estado (status code).
### 25. Get all weekly diets.

 Url:https://us-central1-back-f0378.cloudfunctions.net/api/patientsWeeklyDiets/getAllWeeklyDiets
- Tipo de petición: GET
- Parámetros:
  - NA.
- Restricciones:
  - Key: Authorization
  - Value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - Rut
  - Date

- Respuesta: estado (status code).

### 26. Modify a weekly diet.

 Url:https://us-central1-back-f0378.cloudfunctions.net/api/patientsWeeklyDiets/modifyWeeklyDiets
- Tipo de petición: PUT
- Parámetros:
  - NA.
- Restricciones:
  - Key: Authorization
  - Value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - Rut
  - Date
  - Day
  - Breakfast
  - Lunch
  - Snack
  - Post_training (not mandatory)
  - Dinner

- Respuesta: estado (status code).

### 27. Delete day of weekly diet.

 Url:https://us-central1-back-f0378.cloudfunctions.net/api/patientsWeeklyDiets/deleteWeeklyDiets
- Tipo de petición: DEL
- Parámetros:
  - NA.
- Restricciones:
  - Key: Authorization
  - Value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - Rut
  - Date
  - Day

- Respuesta: estado (status code).

### 28. Delete a week of weekly diet.

 Url:https://us-central1-back-f0378.cloudfunctions.net/api/patientsWeeklyDiets/deleteWeekOfWeeklyDiets
- Tipo de petición: DEL
- Parámetros:
  - NA.
- Restricciones:
  - Key: Authorization
  - Value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - Rut
  - Date

- Respuesta: estado (status code).



### 29. Get statistics of patients
- Url: https://us-central1-back-f0378.cloudfunctions.net/api/patients/getStatistics
- Tipo de petición: GET
- Parámetros:
  - NA.
- Restricciones:
  - Key: Authorization
  - Value: Bearer + Token inicio de sesión del administrador
- Campos necesarios:
  - NA.

- Respuesta: estado (status code), mensaje y datos de cuantificación de alimentación, ciudad, sexo, edad y cantidad de pacientes.
