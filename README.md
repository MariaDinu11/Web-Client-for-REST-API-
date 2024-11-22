Dinu Maria Tatiana - 321CC
Tema 4 PCOM - HTTP, Client REST


Am facut implementarea in c++.


request: 
    Pentru request, am pornit de la codul din laborator si am facut modificarile astfel
incat sa folosesc stringuri si stringstreamuri. Am folosit un singur cookie de autentificare,
si am adaugat in functii token-ul JWT pe care l-am aduagat in mesaj impreuna cu textul precizat
"Authorization: Bearer ".

client:

        Am implementat un client care se conecteaza la serverul dat si permite utilizatorilor sa efectueze 
    diferite comenzi pentru lucrul cu o biblioteca. Programul foloseste HTTP pentru a comunica cu serverul
    si a gestiona raspunsurile.

    In client.cpp am implementat urmatoarele functii:

    cookie_function: care extrage cookie ul din raspuns de la textul "Set-Cookie: " sau pastreaza 
    cookie ul gol daca nu a fost gasit.

    token_function: care extrage token ul din raspuns, il parseaza si il returneaza.

    get_status: care extrage statusul unui raspuns pentru a trata erorile. Converteste in int si 
    il returneaza.

    In main: setez cookie ul si token ul JWT sa fie goale. In bucla while deschid conexiunea cu 
    serverul si citesc de la tastatura comanda asteptata.
    Am cate un if pentru fiecare comanda existenta.
        Daca introduc "register" sau "login" verific sa nu fiu deja autentificat, si citesc username ul
    si parola,  verific sa nu aiba spatii. Formez un json cu ele si trimit mesajul catre server
    Folosind codul de status tartez erorile si cazurile de succes posibile. La login extrag
    cookie ul de sesiune daca utilizatorul s-a autentificat cu succes.
        PENTRU TOATE COMENZILE TRIMIT MESAJUL CATRE SERVER SI IL PRIMESC FOLOSIND FUNCTIILE DEJA 
    DATE IN LABORATOR
        Pentru "enter_library" verific daca sunt logat prin cookie. La succes extrag token ul cu 
    functia token_function.
        Pentru "get_books", "get_book", "add_book" si "delete_book" verific daca am acces la biblioteca 
    prin token. 
        Pentru "get_books" si "get_book" extrag jsonul si il parsez, in cazul de succes.
        Pentru "add_book" citesc datele despre carte si verific daca nu sunt nule si daca pagecount ul este 
    un numar.
        Pentru "delete_book" citesc id ul cartii pe care vreau sa o sterg.
        Pentru "logout" verific daca sunt autentificat, iar daca sunt il deloghez , setez cookie ul si 
    token ul cu "".
        Inchid conexiunea cu serverul.
# Web-Client-for-REST-API-
