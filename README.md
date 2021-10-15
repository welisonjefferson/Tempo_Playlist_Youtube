# Tempo_Playlist_Youtube
Abre a Playlist do youtube e cole no console. 

(function() {
    var playlist = document.querySelectorAll("#contents"),
        timeSeconds = 0,
        timesContainer = null;

    for(var i = 0; i < playlist.length; i++){

        timesContainer = playlist[i].querySelectorAll(".style-scope ytd-thumbnail-overlay-time-status-renderer");

    }

    for(var i = 0; i < timesContainer.length; i++){
        var timeStr = timesContainer[i].innerText,
        timeParts = timeStr.split(":"),
        seconds = 0;
        
        if (timeParts.length > 2)
        {
            seconds = (timeParts[0] * 60 * 60) + (timeParts[1] * 60) + parseInt(timeParts[2]);
        }
        else
        {
            seconds = (timeParts[0] * 60) + parseInt(timeParts[1]);
        }
        
        
        timeSeconds += seconds;
    }

    const segundos = 1;
    const minutos = 60;
    const horas = 3600; //minutos * 60
    const dias = 86400; //horas * 24

     //dias
    if (timeSeconds > dias){
        var dia = Math.floor(timeSeconds / dias);
        timeSeconds = timeSeconds - (dias * dia);
    }else{
        var dia = 0;
    }

    //horas
    if (timeSeconds > horas){
        var hora = Math.floor(timeSeconds / horas);
        timeSeconds = timeSeconds - (horas * hora);
    }else{
        var hora = 0;
    }

    //minutos
    if (timeSeconds > minutos){
        var minuto = Math.floor(timeSeconds / minutos);
        timeSeconds = timeSeconds - (minutos * minuto);
    }else{
        var hora = 0;
    }

    //O resto são os segundos
    var segundo = timeSeconds;

    var horasTotais = dia * 24 + hora;
           
    alert(horasTotais+':'+minuto+':'+segundo);
    //alert('Dias: '+dia+' - Horas: '+hora+' - Minuto: '+minuto);

    
})();
