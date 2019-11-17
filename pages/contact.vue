<template>
  <div>
    <h1>Terminwunsch</h1>
     <hr class="border-t-4 border-blue-500 rounded my-6">

    <div>
      <div class="markdown">
        <p>Wir stehen nach Terminvereinbarung auch abends und samstags zur Verfügung.</p>
        <ul>
          <li><Icon name="icon-check" class="mr-2"/>Kontaktieren Sie uns für kostenlose Beratung mit localen Preisen auf Deutsch.</li>
          <li><Icon name="icon-check" class="mr-2"/>Holen Sie sich ein Angebot für Zahnpflege im Ausland inkl. Transport.</li>
          <li><Icon name="icon-check" class="mr-2"/>Schreiben Sie und noch heute und erhalten Antworten auf Ihre Fragen. Montag bis Samstag um. 9-20</li>
          <li><Icon name="icon-check" class="mr-2"/>Schweizer Natel Nummer: +41 79 50 95 048</li>
        </ul>
        <p>Oder füllen Sie das Formular aus und lassen Sie sich schnell ein unverbindliche Offerte erstellen:</p>
      </div>
      <section>
        <h2>
          <a id="formular" href="#formular">Kontaktformular</a>
        </h2>
        <FormContact/>
      </section>
     </div>
  </div>
</template>

<script>

import Icon from '@/components/Icon'
import FormContact from '@/components/FormContact'

export default {
  components: {
    FormContact,
    Icon
  }
}
</script>
