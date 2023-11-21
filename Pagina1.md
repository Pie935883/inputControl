var nuovaIVA = document.getElementById("nuovaIVA");
var nuovaEmail = document.getElementById("nuovaEmail");
var nuovaPEC = document.getElementById("nuovaPEC");
var nuovaCellulare = document.getElementById("nuovaCellulare");
var nuovaCodiceFiscale = document.getElementById("nuovaCodiceFiscale");
var nuovaCognome = document.getElementById("nuovaCognome");
var nuovaNome = document.getElementById("nuovaNome");
var nuovaDenominazione = document.getElementById("nuovaDenominazione");
const nuovaControlli = [nuovaDenominazione, nuovaNome, nuovaCognome];


nuovaControlli.forEach(addEventListenerVerificaTesto);

addEventListenerVerificaIVA(nuovaIVA);

addEventListenerVerificaCodiceFiscale(nuovaCodiceFiscale);

nuovaEmail.addEventListener("focusout", function z(ev) {
    // mail.style.backgroundColor = 'green';
    compilazioneRecapitiElettronici(nuovaEmail, nuovaPEC);
});

nuovaPEC.addEventListener("focusout", function s(ev) {
    // PEC.style.backgroundColor = 'green';
    //alert('esco PEC');
    compilazioneRecapitiElettronici(nuovaEmail, nuovaPEC);
});


addEventListenerVerificaCellulare(nuovaCellulare);
