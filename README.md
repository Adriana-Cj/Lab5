# Lucrarea de laborator nr. 5. Componentele de securitate în Laravel

## Scopul lucrării

Familiarizarea cu bazele componentelor de securitate în Laravel, cum ar fi autentificarea, autorizarea, protecția împotriva CSRF, precum și utilizarea mecanismelor integrate pentru gestionarea accesului.
Studierea abordărilor dezvoltării sigure, inclusiv crearea rutelor protejate și gestionarea rolurilor utilizatorilor.

## Condiții
În această lucrare de laborator, vom implementa componentele principale de securitate, precum autentificarea, autorizarea, protecția rutelor și gestionarea de bază a rolurilor. În plus, vom configura mecanismul de resetare a parolei și vom explora logarea acțiunilor utilizatorilor.

## Nr. 1. Pregătirea pentru lucru
1. Cream un nou proiect Laravel (dacă nu este instalat) sau continuam cu proiectul anterior.
2. Ne asiguram că variabilele de mediu din fișierul `.env` sunt configurate corect, inclusiv conexiunea la baza de date.

## Nr. 2. Autentificarea utilizatorilor
1. Cream un controller `AuthController` pentru gestionarea autentificării utilizatorilor.
 Cream AuthController: `php artisan make:controller AuthController`
2. Adăugam și implementam metodele pentru înregistrarea, autentificarea și deconectarea utilizatorului:
 - `register()` pentru afișarea formularului de înregistrare.
 ![image](https://github.com/user-attachments/assets/f37a4235-3960-468c-bfa8-397870524346)

 - `storeRegister()` pentru procesarea datelor din formularul de înregistrare.
 ![image](https://github.com/user-attachments/assets/06e8f984-ce84-4890-9e4f-77d34c025cc1)

 - `login()` pentru afișarea formularului de autentificare.
  ![image](https://github.com/user-attachments/assets/65218a0f-b87e-44a5-a45a-c08301eeca2e)

 - `storeLogin()` pentru procesarea datelor din formularul de autentificare.
![image](https://github.com/user-attachments/assets/6c421124-d96f-4944-bf88-639a73b792ef)

3. Cream rute pentru înregistrarea, autentificarea și deconectarea utilizatorului.
4. Actualizam vizualizările pentru formularele de înregistrare și autentificare.
În fișierul `resources/views/auth/register.blade.php` am adaugat:
![image](https://github.com/user-attachments/assets/ff685dd0-a4bf-459d-a95f-a3abebba803d)
![image](https://github.com/user-attachments/assets/d8e30973-2516-45d1-995d-fcd8e0b3cb04)

În fișierul `resources/views/auth/loghin.blade.php` am adaugat:

6. Cream o clasă separată Request pentru validarea datelor de înregistrare sau autentificare sau adăugați validarea direct în controller.
   
În fișierul `app/Http/Requests/Auth/RegisterRequest.php` am adaugat:
![image](https://github.com/user-attachments/assets/cd099e47-558e-44e3-a13d-16a84ae1d291)

În fișierul `app/Http/Requests/Auth/LoginRequest.php` am adaugat:
![image](https://github.com/user-attachments/assets/ffc9abc3-a6b2-4a1d-a6c1-e83ef67e52b1)

6. Verificam dacă înregistrarea și autentificarea utilizatorului funcționează corect.

## Nr. 3. Autentificarea utilizatorilor cu ajutorul componentelor existente
1. Instalam biblioteca Laravel Breeze (sau Fortify, Jetstream) pentru o configurare rapidă a autentificării:
bash php artisan breeze:
`install npm install && npm run dev php artisan migrate`
2. Urmam instrucțiunile de instalare și configurare a pachetului.
3. Verificam dacă rutele `/register`, `/login`, `/logout` funcționează corect.

## Nr. 4. Autorizarea utilizatorilor
1. Implementam o pagină „Panou personal”, accesibilă doar utilizatorilor autentificați.
2. Configuram verificarea accesului la această pagină, adăugând middleware-ul auth în rută sau implementând verificarea în controller.
3. Actualizam vizualizarea paginii „Panou personal” pentru a afișa informațiile disponibile exclusiv utilizatorilor autentificați.

## Nr. 5. Rolurile utilizatorilor
1. Adăugam un sistem de roluri: Administrator și Utilizator.
2. Configuram comportamentul pentru fiecare rol:
 - **Administrator**: are posibilitatea de a vizualiza panourile personale ale tuturor utilizatorilor.
 - **Utilizator**: poate vizualiza doar propriul panou personal.
3. Implementam verificările rolurilor folosind metoda can, Gate sau middleware, pentru a asigura distribuirea corectă a drepturilor de acces.

## Nr. 6. Deconectarea și protecția împotriva CSRF
1. Adăugam un buton pentru deconectarea utilizatorului pe pagină.
2. Asiguram protecția împotriva atacurilor CSRF pe formulare.
3. Verificam că deconectarea utilizatorului funcționează corect și sigur.

## Întrebări de control
**1. Ce soluții integrate pentru autentificare oferă Laravel?**

**2. Ce metode de autentificare a utilizatorilor cunoașteți?**

**3. Care este diferența dintre autentificare și autorizare?**

**4. Cum se asigură protecția împotriva atacurilor CSRF în Laravel?**
