
var cantiereindirizzoCivico = document.getElementById("cantiereindirizzoCivico");
var cantiereCAP = document.getElementById("cantiereCAP");
var cantierecomune = document.getElementById("cantierecomune");
var cantierenumeroNotifica = document.getElementById("cantierenumeroNotifica");
var cantieredataInizio = document.getElementById("cantieredataInizio");
var cantieredataFine = document.getElementById("cantieredataFine");
var cantieredescizione = document.getElementById("cantieredescrizione");
var cantiereCUP = document.getElementById("cantiereCUP");
var cantiereCIG = document.getElementById("cantiereCIG");
var cantierenomeCognome = document.getElementById("cantierenomeCognome");
var cantiereindirizzo = document.getElementById("cantiereindirizzo");
var cantiereCAP1 = document.getElementById("cantiereCAP1");
var cantierecomune1 = document.getElementById("cantierecomune1");
var cantieremail = document.getElementById("cantieremail");
var cantierePEC = document.getElementById("cantierePEC");
var cantiereimportoComplessivo = document.getElementById("cantiereimportoComplessivo");
var cantiereimportoEdili = document.getElementById("cantiereimportoEdili");
var cantiererecapiti = document.getElementById("cantiererecapiti");
var cantierecellulare = document.getElementById("cantierecellulare");
var cantieremail1 = document.getElementById("cantieremail1");
var cantiereorari = document.getElementById("cantiereorari"); 
var cantiereprivato = document.getElementById("cantiereprivato");
var cantierepubblico = document.getElementById("cantierepubblico");
var cantiereTitolare = document.getElementById("cantiereTitolare");
const cantiereControlliCAP = [cantiereCAP, cantiereCAP1];
const cantiereControlliNumero = [cantiereindirizzoCivico, cantiereimportoComplessivo, cantiereimportoEdili, cantiererecapiti];
const cantiereControlliTesto = [cantierecomune, cantierecomune1, cantierenomeCognome, cantiereindirizzo, cantiereTitolare];
const cantiereControlliData = [cantieredataInizio, cantieredataFine];
const cantiereControlliTesto2 = [cantieredescizione, cantiereorari];
//----------------------------------------------------------------

cantiereControlliTesto2.forEach(addEventListenerVerificaTesto2);

cantiereControlliTesto.forEach(addEventListenerVerificaTesto);

cantiereControlliCAP.forEach(addEventListenerVerificaCAP);

addEventListenerVerificaCellulare(cantierecellulare);


cantieremail.addEventListener("focusout", function z(ev) {
// mail.style.backgroundColor = 'green';
compilazioneRecapitiElettronici(cantieremail, cantierePEC);
});

cantierePEC.addEventListener("focusout", function s(ev) {
// PEC.style.backgroundColor = 'green';
//alert('esco PEC');
compilazioneRecapitiElettronici(cantieremail, cantierePEC);
});


controlloformatoemail(cantieremail1.value);
cantieremail1.addEventListener("focusout", function i(ev){ 
var sintassiEmail = controlloformatoemail(cantieremail1.value);
cantieremail1.value = cantieremail1.value.trim();

if(cantieremail1.value.lenght == 0){
    evidenziaErrore(cantieremail1);
}

if(sintassiEmail){
    resettaErrore(cantieremail1);
}
else{
    evidenziaErrore(cantieremail1);
}
});

cantiereControlliNumero.forEach(addEventListenerVerificaNumero);


 /* ------------------------------------- */

function addEventListenerVerificaNumeroNotifica(controllo){
    controllo.addEventListener("focusout", function k(ev){
        wrapperVerificaNumeroNotifica(controllo);
    });
}

function wrapperVerificaNumeroNotifica(controllo){

    controllo.value = controllo.value.trim();

    if(/\d\/\d{2,4}/.test(controllo.value)){
        resettaErrore(controllo);
    }    
    else{
        evidenziaErrore(controllo);
    }
}

addEventListenerVerificaNumeroNotifica(cantierenumeroNotifica);


 /* ------------------------------------- */


cantiereControlliData.forEach(addEventListenerVerificaData);



function pubblicoPrivato(){
    
    if(cantiereprivato.checked == true){
        cantiereCUP.value="";
        cantiereCIG.value="";
        cantiereCUP.hidden = true;
        cantiereCIG.hidden = true;
    }

    else if(cantierepubblico.checked == true){
        cantiereCUP.hidden = false;
        cantiereCIG.hidden = false;
    }

}


