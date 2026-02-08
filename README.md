<!DOCTYPE html>
<html>
<body>

<h2>Mi Asistente</h2>
<button onclick="escuchar()">Hablar</button>
<p id="texto"></p>

<script>
function escuchar(){
  const rec = new webkitSpeechRecognition();
  rec.lang = "es-ES";

  rec.onresult = e=>{
    let mensaje = e.results[0][0].transcript;
    document.getElementById("texto").innerText = mensaje;

    responder(mensaje);
  };

  rec.start();
}

function responder(msg){
  let respuesta = "Hola, en que puedo ayudarte";

  if(msg.toLowerCase().includes("hola"))
    respuesta = "Hola, estoy aquí";

  if(msg.toLowerCase().includes("cómo te llamas"))
    respuesta = "me llamo jarvis";

  if(msg.toLowerCase().includes("saluda a la clase"))
    respuesta = "es un placer para mi saludar a esta clase,espero la pasen bien y aprendan de la mano de su profesor";


  const voz = new SpeechSynthesisUtterance(respuesta);
  speechSynthesis.cancel();
  speechSynthesis.speak(voz);
}
</script>

</body>
</html>
