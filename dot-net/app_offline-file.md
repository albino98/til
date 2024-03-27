# File app_offline web application .NET

Per rendere temporaneamente indisponibile un'applicazione web .NET inserire nella root della cartella del progetto IIS un file chiamato app_offline.htm come per esempio quello di seguito.

Quando viene aggiunto questo file, l'intera applicazione viene disattivata e nessuna delle risorse è disponibile (viene restituito error 503 su ogni risorsa e mostrata la pagina).

Se si vuole aggiungere uno stile, il codice css deve essere inline, inserito quindi nel file. Per le immagini è necessario convertirle in base64.

~~~

<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Offline</title>
</head>
<body style="margin:3em;font-family:sans-serif">
  <h2>Offline</h2>
  <p>This site is offline for maintenance.</p>
  <!--       
    Adding some hidden content so that IE "Friendly Errors" don't keep
    this message from displaying. (It will show a "friendly" 404
    error if the content isn't at least 512 bytes.)
    This is mostly a problem for IE6 which has "Friendly Errors" on by default.
    See http://weblogs.asp.net/scottgu/App_5F00_Offline.htm-and-working-around-the-_2200_IE-Friendly-Errors_2200_-feature
    
    <h2>This site is offline.</h2>
    <h2>This site is offline.</h2>
    <h2>This site is offline.</h2>
    <h2>This site is offline.</h2>
    <h2>This site is offline.</h2>
    -->
</body>
</html>

~~~
