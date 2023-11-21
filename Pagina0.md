 var controlliNuovaImpresa = "nuovaIVA;nuovaEmail;nuovaPEC;nuovaCodiceFiscale;nuovaCognome;nuovaNome;nuovaDenominazione";
    var controlliNuovoCantiere = "cantiereindirizzoCivico;cantiereCAP;cantierecomune;cantierenumeroNotifica;cantieredataInizio;cantieredataFine;cantieredescrizione;cantierenomeCognome;cantiereindirizzo;cantiereCAP1;cantierecomune1;cantieremail;cantierePEC;cantiereimportoComplessivo;cantiereimportoEdili;cantiererecapiti;cantieremail1;cantiereorari;cantiereTitolare";
    var controlliNuovoSubappalto = "subappaltoTitolare;subappaltoCantiere;subappaltoDenominazione;subappaltoCodiceFiscale;subappaltoIVA;subappaltoDataInizio;subappaltoDataFine";
    //var controlliNuovoSubappalto = "subappaltoTitolare;subappaltoCantiere;subappaltoDenominazione;subappaltoCodiceFiscale;subappaltoIVA;subappaltoDataInizio;subappaltoDataFine";
    //SF BEBUG purpuoses var controlliNuovoSubappalto = "subappaltoTitolare";
    var controlliInserimentoOre = "oreTitolare;orecantiere;oreanno;orenomeCognome;oreore";
    var controlliAttestazioneCongruita = "congruitadataChiusura;congruitanomeCognome;congruitacodiceFiscale;congruitaPEC;congruitacantiere;congruitaTitolare";

    function evidenziaErrore(controllo) {
            controllo.style.backgroundColor = 'red';
        }

    function resettaErrore(controllo) {
            controllo.style.backgroundColor = 'white';
        }



    /* --------------------------------------------------- */
    // Codice Fiscale 

    function addEventListenerVerificaCodiceFiscale(controllo) {
        controllo.addEventListener("focusout", function b(ev) {
            wrapperVerificaCodiceFiscale(controllo);
        });
    }

    function wrapperVerificaCodiceFiscale(controllo) {
            if (!/^(?:[A-Z][AEIOU][AEIOUX]|[AEIOU]X{2}|[B-DF-HJ-NP-TV-Z]{2}[A-Z]){2}(?:[\dLMNP-V]{2}(?:[A-EHLMPR-T](?:[04LQ][1-9MNP-V]|[15MR][\dLMNP-V]|[26NS][0-8LMNP-U])|[DHPS][37PT][0L]|[ACELMRT][37PT][01LM]|[AC-EHLMPR-T][26NS][9V])|(?:[02468LNQSU][048LQU]|[13579MPRTV][26NS])B[26NS][9V])(?:[A-MZ][1-9MNP-V][\dLMNP-V]{2}|[A-M][0L](?:[1-9MNP-V][\dLMNP-V]|[0L][1-9MNP-V]))[A-Z]$/i.test(controllo.value)) {
                evidenziaErrore(controllo);
            } else {
                resettaErrore(controllo);
            }
    }

    /* --------------------------------------------------- */

    var chlEmailConoscenza = document.getElementById("chlEmailConoscenza");
    var txtemailConoscenza = document.getElementById("txtemailConoscenza");

    //txtemailConoscenza.hidden = true;


    function controlloCasella(){
        
        if(chlEmailConoscenza.checked){
        console.log("sono chechek");
        txtemailConoscenza.hidden = false;
        /* ------------------------------------------ */
        txtemailConoscenza.addEventListener("focusout", function i(ev){ 
            var sintassiEmail = controlloformatoemail(txtemailConoscenza.value);
            txtemailConoscenza.value = txtemailConoscenza.value.trim();
        
            if(txtemailConoscenza.value.lenght == 0){
                evidenziaErrore(txtemailConoscenza);
            }
        
            if(sintassiEmail){
                resettaErrore(txtemailConoscenza);
            }
            else{
                evidenziaErrore(txtemailConoscenza);
            }
        });
        }
        else{
            console.log("non sono checked");
            txtemailConoscenza.value ="";
            txtemailConoscenza.hidden = true;
        
        }
    }


    function mostraInformativa() {
        var divInformativa = document.getElementById("informativaPrivacy");
        if (divInformativa.style.display === "none") {
        divInformativa.style.display = "block";
        } else {
        divInformativa.style.display = "none";
        }
    }



    /* --------------------------------------------------- */
    // verifica formale compilazione partita IVA
    function addEventListenerVerificaIVA(controllo) {
        controllo.addEventListener("focusout", function n(ev) {
            wrapperVerificaIVA(controllo);
        });
    }

    function wrapperVerificaIVA(controllo) {
            if ((/^[0-9]+$/.test(controllo.value)) && (controllo.value.length == 11)) {
                resettaErrore(controllo);
            } else {
                evidenziaErrore(controllo);
            }
    }

    /* --------------------------------------------------- */
    // verifica che il controllo non sia vuoto - testo generico

    function addEventListenerVerificaTesto(controllo) {
        controllo.addEventListener("focusout", function b(ev) {
            wrapperVerificaTesto(controllo);
        });
    }


    function wrapperVerificaTesto(controllo) {
            controllo.value = controllo.value.trim();

        if ((/[0-9]/.test(controllo.value)) || controllo.value.length == 0) {
                evidenziaErrore(controllo);
            } else {
                resettaErrore(controllo);
            }
    }

    function addEventListenerVerificaTesto2(controllo) {
        controllo.addEventListener("focusout", function x(ev) {
            wrapperVerificaTesto2(controllo);
        });
    }

    function wrapperVerificaTesto2(controllo){
        controllo.value = controllo.value.trim();

            if (controllo.value.length == 0) {
                evidenziaErrore(controllo);
            } else {
                resettaErrore(controllo);
            }
    }



    /* --------------------------------------------------- */


    function addEventListenerVerificaData(controllo){
        controllo.addEventListener("focusout", function p(ev) {
            wrapperVerificaData(controllo);
        });
    }

    function wrapperVerificaData(controllo){

    controllo.value = controllo.value.trim();
        if (isNaN(controllo)){
                evidenziaErrore(controllo);
        }
        if(/\d{4}\-\d{2}\-\d{2}/.test(controllo.value)){
                console.log("sono nella regex");
                resettaErrore(controllo);
            }
        
    }





    /*

    function verificaData(data) {

        data.addEventListener("focusout", function p(ev) {
            if (isNaN(data) || data.value == null)
                //alert("Il valore inserito non è una data valida");
                evidenziaErrore(data);
            else {
                resettaErrore(data);
            }
        });

    }

    /* --------------------------------------------------- */

    function controlloformatoemail(indirizzo) {
        var esito = true
        indirizzo = indirizzo.trim();
        if (indirizzo.length == 0) {
            esito = false;
        }
        //if (!/^[a-zA-Z0-9.!#$%&'*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/.test(indirizzo)) {
        if(!/^[A-z0-9\.\+_-]+@[A-z0-9\._-]+\.[A-z]{2,6}$/.test(indirizzo)){
            esito = false;
        }
        return (esito);
    }

    /*---------------------------------------------------*/
    // verifica cellulare numerico e valorizzato

    function addEventListenerVerificaCellulare(controllo) {
        controllo.addEventListener("focusout", function f(ev) {
            wrapperVerificaCellulare(controllo);
        });
    }

    function wrapperVerificaCellulare(controllo) {
            controllo.value = controllo.value.trim();

            if (((/^[0-9]+$/.test(controllo.value)) || controllo.value.length == 0)) {
                resettaErrore(controllo);
            } else {
                evidenziaErrore(controllo);
            }
    }

    /* ----------------------------------------------- */

    function addEventListenerVerificaNumero(controllo) {
        controllo.addEventListener("focusout", function f(ev) {
            wrapperVerificaNumero(controllo);
        });
    }

    function wrapperVerificaNumero(controllo) {
            controllo.value = controllo.value.trim();

            if (((/^[0-9]+$/.test(controllo.value)))) {
                resettaErrore(controllo);
            } else if(controllo.value.lenght == 0) {
                evidenziaErrore(controllo);
            }
            else{
                evidenziaErrore(controllo);
            }
    }



    /* --------------------------------------------------- */


    function addEventListenerVerificaCAP(controllo){
        controllo.addEventListener("focusout", function f(ev) {
                wrapperVerificaCAP(controllo);
        });

    }

    function wrapperVerificaCAP(controllo){

        controllo.value = controllo.value.trim();

        if (((/^[0-9]+$/.test(controllo.value)) && controllo.value.length == 5)) {
            resettaErrore(controllo);
        } else {
            evidenziaErrore(controllo);
        }

    }





    /* --------------------------------------------------- */


    function compilazioneRecapitiElettronici(email, pec) {
        var statoEmail = false;
        var statoPEC = false;
        email.value = email.value.trim();
        pec.value = pec.value.trim();
        var sintassiEmail = controlloformatoemail(email.value);     // tring testo inviato
        var sintassiPEC = controlloformatoemail(pec.value);

        if (email.value.length == 0)   //  se email == vuota
        {
            resettaErrore(email);            //email bianca
            statoEmail = false;
        } else {
            if (sintassiEmail)  //se email == valida
            {
                resettaErrore(email);   // sfondo email bianco
                statoEmail = true;
            } else {
                evidenziaErrore(email);    //        email rossa
                statoEmail = false;
            }
        }
        // *************************************** 
        if (pec.value.length == 0)   //  se pec == vuota
        {
            resettaErrore(pec);            //pec bianca
            statoPEC = false;
        } else {
            if (sintassiPEC)  //se PEC == valida
            {
                resettaErrore(pec);   // sfondo pec bianco
                statoPEC = true;
            } else {
                evidenziaErrore(pec);    //       pec rossa
                statoPEC = false;
            }
        }
        // *************************************

        if (statoEmail == false && statoPEC == false) {
            evidenziaErrore(email);    //        email rossa
            evidenziaErrore(pec);      //      PEC rossa
        }
    }
