# Καλώς ήρθατε στην επέκταση σας για το VS Code

## Τι περιέχει ο φάκελος

* Αυτός ο φάκελος περιέχει όλα τα αρχεία που χρειάζεστε για την επέκτασή σας.
* `package.json` - αυτό είναι το αρχείο manifest, στο οποίο δηλώνετε την επέκταση και την εντολή σας.
  * Το δείγμα προσθήκης καταχωρεί μια εντολή και ορίζει τον τίτλο και το όνομα της εντολής. Με αυτές τις πληροφορίες, το VS Code μπορεί να εμφανίσει την εντολή στη λίστα εντολών. Δεν χρειάζεται ακόμα να φορτώσει την προσθήκη.
* `src/extension.ts` - αυτό είναι το κύριο αρχείο, όπου θα παρέχετε την υλοποίηση της εντολής σας.
  * Το αρχείο εξάγει μια συνάρτηση, `activate`, η οποία καλείται την πρώτη φορά που ενεργοποιείται η επέκτασή σας (σε αυτή την περίπτωση με την εκτέλεση της εντολής). Μέσα στη συνάρτηση `activate` καλούμε τη `registerCommand`.
  * Περνάμε τη συνάρτηση που περιέχει την υλοποίηση της εντολής ως δεύτερη παράμετρο στη `registerCommand`.

## Ρύθμιση

* Εγκαταστήστε τις προτεινόμενες επεκτάσεις (amodio.tsl-problem-matcher, ms-vscode.extension-test-runner και dbaeumer.vscode-eslint).

## Ξεκινήστε αμέσως

* Πατήστε `F5` για να ανοίξετε ένα νέο παράθυρο με φορτωμένη την επέκτασή σας.
* Εκτελέστε την εντολή σας από τη λίστα εντολών πατώντας (`Ctrl+Shift+P` ή `Cmd+Shift+P` σε Mac) και πληκτρολογώντας `Hello World`.
* Τοποθετήστε σημεία διακοπής στον κώδικά σας μέσα στο `src/extension.ts` για να αποσφαλματώσετε την επέκτασή σας.
* Βρείτε την έξοδο της επέκτασής σας στην κονσόλα αποσφαλμάτωσης.

## Κάντε αλλαγές

* Μπορείτε να επανεκκινήσετε την επέκταση από τη γραμμή εργαλείων αποσφαλμάτωσης αφού κάνετε αλλαγές στο `src/extension.ts`.
* Μπορείτε επίσης να επαναφορτώσετε (`Ctrl+R` ή `Cmd+R` σε Mac) το παράθυρο του VS Code με την επέκτασή σας για να φορτώσετε τις αλλαγές σας.

## Εξερευνήστε το API

* Μπορείτε να ανοίξετε το πλήρες σύνολο του API μας ανοίγοντας το αρχείο `node_modules/@types/vscode/index.d.ts`.

## Εκτελέστε δοκιμές

* Εγκαταστήστε το [Extension Test Runner](https://marketplace.visualstudio.com/items?itemName=ms-vscode.extension-test-runner).
* Εκτελέστε το task "watch" μέσω της εντολής **Tasks: Run Task**. Βεβαιωθείτε ότι αυτό εκτελείται, αλλιώς οι δοκιμές μπορεί να μην αναγνωριστούν.
* Ανοίξτε την προβολή Testing από τη γραμμή δραστηριοτήτων και κάντε κλικ στο κουμπί "Run Test" ή χρησιμοποιήστε τη συντόμευση `Ctrl/Cmd + ; A`.
* Δείτε τα αποτελέσματα των δοκιμών στην προβολή Test Results.
* Κάντε αλλαγές στο `src/test/extension.test.ts` ή δημιουργήστε νέα αρχεία δοκιμών μέσα στον φάκελο `test`.
  * Ο παρεχόμενος runner δοκιμών θα λάβει υπόψη μόνο αρχεία που ταιριάζουν με το μοτίβο ονόματος `**.test.ts`.
  * Μπορείτε να δημιουργήσετε φακέλους μέσα στον φάκελο `test` για να οργανώσετε τις δοκιμές σας όπως θέλετε.

## Προχωρήστε παραπέρα

* Μειώστε το μέγεθος της επέκτασης και βελτιώστε τον χρόνο εκκίνησης [συμπιέζοντας την επέκτασή σας](https://code.visualstudio.com/api/working-with-extensions/bundling-extension?WT.mc_id=aiml-137032-kinfeylo).
* [Δημοσιεύστε την επέκτασή σας](https://code.visualstudio.com/api/working-with-extensions/publishing-extension?WT.mc_id=aiml-137032-kinfeylo) στην αγορά επεκτάσεων του VS Code.
* Αυτοματοποιήστε τις διαδικασίες κατασκευής ρυθμίζοντας [Συνεχή Ενσωμάτωση](https://code.visualstudio.com/api/working-with-extensions/continuous-integration?WT.mc_id=aiml-137032-kinfeylo).

**Αποποίηση ευθύνης**:  
Αυτό το έγγραφο έχει μεταφραστεί χρησιμοποιώντας υπηρεσίες αυτόματης μετάφρασης που βασίζονται σε τεχνητή νοημοσύνη. Παρόλο που καταβάλλουμε προσπάθειες για ακρίβεια, παρακαλούμε να έχετε υπόψη ότι οι αυτόματες μεταφράσεις ενδέχεται να περιέχουν λάθη ή ανακρίβειες. Το αρχικό έγγραφο στη μητρική του γλώσσα θα πρέπει να θεωρείται η έγκυρη πηγή. Για κρίσιμες πληροφορίες, συνιστάται επαγγελματική μετάφραση από άνθρωπο. Δεν φέρουμε ευθύνη για τυχόν παρεξηγήσεις ή εσφαλμένες ερμηνείες που προκύπτουν από τη χρήση αυτής της μετάφρασης.