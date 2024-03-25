# Mush YouTube demo

Mush YouTube demo in itailano


## Esempi di utilizzo

### Progetto che richiede l'utilizzo di JQ

Spesso i progetti possono richiedere tool da integrare con l'esecuzione dei propri script, per garantire che i tool siano presenti, bisogna dichiarare la dipendenza nel Manifest.toml come segue

```toml
[package]
name = "my-project"
version = "0.1.0"
edition = "2022"

[dependencies]
## Questo indica al sistema di scaricare JQ attraverso il registry "apt"
jq = "apt jq"
```

Mush supporta multipli registry, quindi andrebbero specificati più registry attraverso la seguente sinstassi

```toml
jq = "apt jq | yum jq | apk jq"
```

Dato però che, Mush gestisce anche un registry autonomo, sarà possibile mantenere un pacchetto Mush sul registry pubblico, che ha come scopo quello di tenere aggiornato il Manifest.toml di JQ che in maniera più ambia possibile installi JQ scegliendo in maniera opportuna il registry di installazione. Se tale pacchetto esiste, e viene mantenuto aggiornato, per installare JQ basterebbe semplicemente il seguente codice.

```toml
jq = "mush jq"
```

In questo modo, dopo il seguente comando:

```shell
mush build
```

Verranno installate le dipendenze, o verrano verificate se già presenti nel sistema, nel caso di installazione con richiesta di permessi verra mostrato un wanrnig e le indicazione per procedere con l'installazione (probabilmente invitando a fare un `sudo mush build`)


