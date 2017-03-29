![](https://www.wikirails.com/wp-content/uploads/2017/03/wikirails-logo-git-wide.png)

# Come installare mac OS Sierra su Windows con VirtualBox

Non è fantascienza! Installare Mac OS su Windows è possibile, segui questi semplici passaggi e scopri come Installare Mac OS Sierra su Windows sia davvero facile.

&nbsp;
## **Occorrente**
* VirtualBox (se non hai mai installato una virtual machine, vedi [come installare Oracle VM VirtualBox su Windows](https://www.wikirails.com/it/installare-oracle-vm-virtualbox-windows)
* [Immagine di Mac OS Sierra](https://drive.google.com/open?id=0B-NP0UyxvVoDaGFicEI4V3Y5VzA)

&nbsp;
# **Setup della macchina virtuale**
Il primo passaggio è quello di creare un disco virtuale per eseguire l’installazione di Sierra.
## **Passo 1. Crea una VirtualMachine**
Apri VirtualBox, e crea un nuovo disco, dal menu in alto seleziona **Nuova**

* **Nome**:Mac OS Sierra
* **Tipo**: Mac OS X
* **Versione**: Mac OS X (64bit)

<img class="aligncenter size-full wp-image-576" src="https://www.wikirails.com/wp-content/uploads/2017/03/Create-new-VirtualImage.png" alt="Come installare Mac OS Sierra su Windows - Create new Virtaul Image" width="100%" />

&nbsp;
## **Passo 2. Scegli la quantità di memoria**
Il prossimo passo è selezionare la quantità di memoria RAM che verrà allocata per l’utilizzo della VM. Il minimo indicato è almeno 4GB (4096MB).
<img class="aligncenter size-full wp-image-575" src="https://www.wikirails.com/wp-content/uploads/2017/03/chose-amount-of-merory-ram.png" alt="Scegli la quantità di memoria RAM da utilizzare" width="100%" />

&nbsp;
## **Passo 3. Scegli il tipo di disco fisso**
Nella selezione puoi decidere se creare un nuovo disco fisso o usare quello scaricato (Scegli usa disco fisso virtuale esistente e seleziona il percorso dell’immagine .mdk), infine premi **Crea**.
<img class="aligncenter size-full wp-image-574" src="https://www.wikirails.com/wp-content/uploads/2017/03/chose-virtaul-disk.png" alt="Scegli il tipo di disco fisso da utilizzare" width="100%" />

&nbsp;
## **Passo 4. Impostazioni avanzate**
Dopo aver creato la macchina virtuale, bisogna configurare alcune impostazioni avanzate, per la scelta del video e l’uso dei processori.
Dalla schermata principale di VirtualBox premi il **tasto destro** del mouse sulla nuova macchina creata poi seleziona **Impostazioni…**
<img class="aligncenter size-full wp-image-573" src="https://www.wikirails.com/wp-content/uploads/2017/03/open-new-virtual-disk-settings.png" alt="seleziona il nuovo Virtual Drive e modifica le impostazioni avanzate" width="100%" />

&nbsp;
## **Passo 5. Imposta il chipset della scheda madre**
Entra nel menu laterale **Sistema &gt; Scheda madre**

* **Ordine di Avvio**: Disabilita il floppy
* **Chipset**: ICH9
* **Tipo di puntamento**: Tavoletta ottica
* **Funzionalità estese**:
  *Abilita I/O APIC
  *Abilita EFI
  *Abilita Orologio Hardware



<img class="aligncenter size-full wp-image-572" src="https://www.wikirails.com/wp-content/uploads/2017/03/select-ic9-processor.png" alt="seleziona come tipo di processore IC9 e disabilita il Floppy disk" width="100%" />

&nbsp;
## **Passo 5. Imposta i processori da utilizzare**
Per rendere possibile l’installazione di Sierra occorre impostare almeno 2 processori.
Dalla seconda scheda **Processori** muovere il cursore almeno su due CPU.
<img class="aligncenter size-full wp-image-591" src="https://www.wikirails.com/wp-content/uploads/2017/03/use-two-or-more-core.png" alt="scegli di utilizzare almeno due processori" width="100%" />

&nbsp;
## **Passo 6. Imposta lo schermo**
Dal memu di sinistra passa alla scheda **Schermo**, poi al centro seleziona come memoria video 128MB
<img class="aligncenter size-full wp-image-590" src="https://www.wikirails.com/wp-content/uploads/2017/03/set-video-memory-to-120MB.png" alt="imposta la quantità di memoria video a 128MB" width="100%" />

&nbsp;
## **Passo 7. Imposta la Rete**
Come impostazione finale è il momento della rete LAN, se vuoi che il tuo nuovo sistema Mac acceda ad internet. Dal menu laterale di sinistra, seleziona la scheda **Rete** &gt; **Scheda 1**

* **Connessione**: NAT
* **Espandi il menu Avanzate**
  * **Tipo di Scheda**: Intel PRO/1000 MT Server (8254SEM)
  * **Cavo connesso**: Abilitato


<img class="aligncenter size-full wp-image-589" src="https://www.wikirails.com/wp-content/uploads/2017/03/set-NAT-adapter.png" alt="imposta la rete NAT" width="100%" />
**Passo 8. Impostazioni aggiuntive**

Prima di procedere all’installazione, l’ultimo passo è quello di eseguire alcuni comandi dalla console di Windows (se non sai come avviare la console vedi <a href="https://www.wikirails.com/it/come-aaprire-la-console-di-windows/" target="_blank">come aprire la console di Windows</a>).

Posizionati nella directory di Virtualbox ed esegui questi comandi (copiali ed incollali nel prompt)

**Comandi per VirtualBox 5.x**
<pre>
cd "C:\Program Files\Oracle\VirtualBox\"

VBoxManage.exe modifyvm "Mac OS Sierra" --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
&nbsp;
</pre>
**Comandi per VirtualBox 4.x**
<pre>
cd "C:\Program Files\Oracle\VirtualBox\"

VBoxManage.exe modifyvm "Mac OS Sierra" --cpuidset 00000001 000306a9 04100800 7fbae3ff bfebfbff

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "MacBookPro11,3"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"

VBoxManage setextradata "Mac OS Sierra" "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1
</pre>
&nbsp;

**NOTE**: se hai aggiunto la macchina virtuale con nome diverso da **Mac OS Sierra**, cambia all’interno dei doppi apici tutte le occorrenze di Mac OS Sierra con il nome che gli hai dato.

&nbsp;
# **Installazione di Mac OS Sierra**
Ora è il momento di passare alla fase di installazione di Sierra.
## **Passo 1. Avvia la macchina virtuale**
Dalla schermata principale di VirtualBox seleziona Mac OS Sierra e poi **Avvia**.
<img class="aligncenter size-full wp-image-588" src="https://www.wikirails.com/wp-content/uploads/2017/03/sierra-starting.png" alt="attendi l'avvio dell'installazione di Mac OS Sierra" width="100%" />

&nbsp;
## **Passo 2. Scelta della paese**
La prima impostazione da eseguire, è la scelta del Paese, seleziona quindi la lingua in cui preferisci usare il tuo Mac.
<img class="aligncenter size-full wp-image-587" src="https://www.wikirails.com/wp-content/uploads/2017/03/welcome-to-sierra-installation.png" alt="seleziona la tua lingua preferita" width="100%" />

&nbsp;
## **Passo 3. Scelta della tastiera**
Dopo la scelta del paese, scegli il layout della tua tastiera e procedi.
<img class="aligncenter size-full wp-image-586" src="https://www.wikirails.com/wp-content/uploads/2017/03/select-keyboard-layout.png" alt="scegli il layout della tua tastiera" width="100%" />

&nbsp;
## **Passo 4. Importazione**
In questo caso è possibile importare informazioni da altri Mac, nel caso di una nuova VM, scegli l’ultima voce **Non trasferire nessuna informazione ora**.
<img class="aligncenter size-full wp-image-585" src="https://www.wikirails.com/wp-content/uploads/2017/03/dont-transfer-information.png" alt="scegli se hai delle importazioni da fare da un altro Mac" width="100%" />

&nbsp;
## **Passo 5. Abilita la localizzazione**
Ora è possibile abilitare la localizzazione di Apple, in base alle tue preferenze scegli se Abilitare o meno questa funzionalità.
<img class="aligncenter size-full wp-image-584" src="https://www.wikirails.com/wp-content/uploads/2017/03/location-service.png" alt="scegli se abilitare o meno la localizzazione" width="100%" />

&nbsp;
## **Passo 6. Collega il tuo Apple ID**
Se sei già in possesso di un Apple ID, puoi collegarlo al tuo account, in ogni caso puoi creare un ID Apple in qualsiasi momento. Nel caso vuoi accede a Sierra senza collegare nessun Account, seleziona la voce **Non Accedere**
<img class="aligncenter size-full wp-image-583" src="https://www.wikirails.com/wp-content/uploads/2017/03/login-with-appleid.png" alt="collaga il tuo account Apple" width="100%" />

&nbsp;
## **Passo 7. Accetta i termini di licenza**
L’unica opzione che hai per continuare l’installazione è accettare i termini e le condizioni di Apple, quindi **Accetta** e **Continua**.
<img class="aligncenter size-full wp-image-582" src="https://www.wikirails.com/wp-content/uploads/2017/03/agree-with-term-of-service.png" alt="accetta i termini e le condizioni del servizio Apple" width="100%" />

&nbsp;
## **Passo 8. Crea un nuovo account utente**
Inserisci le informazione dell’utente che deve accedere a questa macchina
<img class="aligncenter size-full wp-image-581" src="https://www.wikirails.com/wp-content/uploads/2017/03/setup-computer-account.png" alt="crea il nuovo utente per accedere a Sierra" width="100%" />

&nbsp;
## **Passo 9. Diagnostica ed errori**
Se vuoi che Apple sia in grado di monitorare il tuo Sistema operativo, e riportare eventuali crash al centro assistenza, attiva queste due opzioni.
<img class="aligncenter size-full wp-image-580" src="https://www.wikirails.com/wp-content/uploads/2017/03/diagnostic-and-usage.png" alt="scegli se abilitare o meno i rapporti di Apple" width="100%" />

&nbsp;
## **Passo 10. Siri**
Scegli se vuoi abilitare o meno Siri, l’assistente vocale di Apple.
<img class="aligncenter size-full wp-image-579" src="https://www.wikirails.com/wp-content/uploads/2017/03/enable-siri.png" alt="scegli se vuoi abilitare Siri" width="100%" />

&nbsp;
## **Passo 11. Attendi che l’installazione venga finalizzata**
<img class="aligncenter size-full wp-image-580" src="https://www.wikirails.com/wp-content/uploads/2017/03/diagnostic-and-usage.png" alt="Attendi che l’installazione venga finalizzata" width="100%" />
Al termine goditi il fantastico sistema operativo Mac OS Sierra, comodamente dal tuo Windows.
<img class="aligncenter size-full wp-image-577" src="https://www.wikirails.com/wp-content/uploads/2017/03/sierra-is-ready.png" alt="Mac OS Sierra è pronto per essere usato su Windows" width="100%" />
Ecco come Installare Mac OS X Sierra su Windows è veramente semplice.

&nbsp;
# **Collegamenti Utili**
* [Sito ufficiale di VM VirtualBox](https://www.virtualbox.org/)
* [Come installare VirtualBox su Windows](https://www.wikirails.com/it/installare-oracle-vm-virtualbox-windows/)
* [Virtual hard drive Mac OS Sierra](https://drive.google.com/open?id=0B-NP0UyxvVoDaGFicEI4V3Y5VzA)
* [Come aprire la console di Windows](https://www.wikirails.com/it/come-aaprire-la-console-di-windows/)
&nbsp;
