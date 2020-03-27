<template>
  <v-container fluid>
    <v-row
      row
      wrap
      align="center"
      justify="center"
      class="mt-12"
    >
      <v-flex xs8>
        <v-card
          tile
          width="500"
          class="pb-3"
        >
          <!-- <v-app-bar
            color="yellow"
            height="200"
          >
            <span class="caption">
              User Account Control
            </span>
            <v-spacer></v-spacer>
            <v-icon class="black--text" small>{{ icons.mdiClose }}</v-icon>
            <template v-slot:extension>
              <p class="headline">Do you want to allow this app from an unknown publisher to make changes to your device?</p>
            </template>
          </v-app-bar> -->
          <v-sheet height="150" color="amber accent-2">
            <v-layout row wrap pl-3>
              <v-flex xs11>
                <span class="caption pl-3">
                User Account Control
                </span>
              </v-flex>
              <v-flex xs1 justify="end" align="right">
                
                <v-icon class="black--text">{{ icons.mdiClose }}</v-icon>
              </v-flex>
              <!-- <v-spacer></v-spacer> -->
            <!-- </v-system-bar> -->
              <v-flex xs12 ma-3 pr-5>
                <p class="headline">Do you want to allow this app from an unknown publisher to make changes to your device?</p>
              </v-flex>
            </v-layout>
          </v-sheet>
          <v-card-title class="headline">
            YoutubeDownloader.exe
          </v-card-title>
          <v-card-text class="my-0 py-0">
            Publisher: Unknown
          </v-card-text>
          <v-card-text class="my-0 py-0">
            File origin: Hard drive on this computer
          </v-card-text>
          <v-card-text class="my-0 py-0">
            Program location: "C:\Users\me\Downloads\YoutubeDownloader.exe"
          </v-card-text>
          <v-card-text class="my-0 py-0 blue--text darken-1">
            Change when these notifications appear
          </v-card-text>
          <v-card-text class="blue--text darken-1">
            Hide details
          </v-card-text>
          <v-card-actions>
            <v-layout row>
              <v-flex xs6 pl-5 pr-1>
                <v-btn
                  tile
                  block
                  elevation="0"
                  color="grey lighten-2"
                >
                  <!-- @click.stop="dialog = true" -->
                  <!-- Learn More -->
                  Yes
                </v-btn>
              </v-flex>
              <v-flex xs6 pl-1 pr-5>
                <v-btn
                  tile
                  block
                  elevation="0"
                  color="grey lighten-2"
                >
                  No
                </v-btn>
              </v-flex>
            </v-layout>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-row>
    <v-dialog
      v-model="dialog"
      max-width="600"
    >
      <v-card tile>
        <v-card-title class="headline">Why do you want to ignore the warning?</v-card-title>

        <v-card-text>
          <v-btn
            color="blue lighten-3"
            @click="understandDialog = true"
          >
            I do not understand this warning
          </v-btn>
        </v-card-text>

        <v-card-text>
          <v-btn
            color="blue lighten-3"
            @click="beforeDialog = true"
          >
            I have used this type of app before
          </v-btn>
        </v-card-text>
        <v-card-text>
          <v-btn
            color="blue lighten-3"
            @click="harmDialog = true"
          >
            I do not think this app will harm my computer
          </v-btn>
        </v-card-text>

        <!-- <v-card-actions>
          <v-spacer></v-spacer>


          <v-btn
            color="green darken-1"
            
            @click="dialog = false"
          >
            Back To Safety
          </v-btn>
        </v-card-actions> -->
      </v-card>
    </v-dialog>
    <v-dialog
      v-model="understandDialog"
      max-width="600"
    >
      <v-card tile
      >
        <!-- <v-card-title class="headline">I do not understand</v-card-title> -->
        <v-card-title class="headline"></v-card-title>
        <v-card-text>
          <v-img src="../assets/bad-guy.png" />
        </v-card-text>
        <v-card-text class="body-1 black--text">
          YoutubeDownloader.exe is not sourced from a verified Microsoft partner.
          Think of a stranger <strong>(the untrusted app)</strong> trying to gain access to your house
          <strong>(your computer)</strong>.
          Would you prefer handing over the key 
          <strong>(allow permission to access your computer)</strong>
          or stop him right away <strong>(block permission)</strong>?
        </v-card-text>

        <v-card-actions>


          <v-btn
            color="red darken-1 white--text"
            @click="understandDialog = false; dialog = false;"
          >
            Understand Risk and Proceed
          </v-btn>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1  white--text"
            
            @click="understandDialog = false; dialog = false;"
          >
            Back To Safety
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-dialog
      v-model="beforeDialog"
      max-width="600"
    >
      <v-card tile
      >
        <v-card-title class="headline"></v-card-title>
        <v-card-text>
          <v-img src="../assets/malware.jpg" />
        </v-card-text>

        <v-card-text class="body-1 black--text">
          Familiarity with certain types of apps does not necessarily mean that all of them are safe.
          <strong>Hackers often inject malicious software into familiar tools</strong> to steal information.
          <!-- The cost of cybercrime has reached more than $2 trillion. -->
          On average a cybercrime incident costs $2,500.
        </v-card-text>
        <!-- <v-card-text>
          Just because you have used this type of app before does not guarantee that the one you are currently trying to install is malware free.
          Always ensure that you completely trust the source of the app.
        </v-card-text> -->

        <v-card-actions>
          <v-btn
            color="red darken-1 white--text"
            @click="beforeDialog = false; dialog = false;"
          >
            Understand Risk and Proceed
          </v-btn>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1 white--text"
            
            @click="beforeDialog = false; dialog = false;"
          >
            Back To Safety
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-dialog
      v-model="harmDialog"
      max-width="600"
    >
      <v-card tile
      >
        <v-card-title class="headline"></v-card-title>

        <v-card-text>
          <v-img src="../assets/confusion.png" />
        </v-card-text>


        <v-card-text class="body-1 black--text">
          There is a high likelyhood that apps installed from third parties will harm your computer since
          <strong>cyber-attacks occur every 39 seconds.</strong> 
          If you succumb to a cyber-attack you could lose <strong>personal data</strong>, or have your <strong>financial information stolen.</strong>
        </v-card-text>

        <v-card-actions>
          <v-btn
            color="red darken-1 white--text"
            @click="harmDialog = false; dialog = false;"
          >
            Understand Risk and Proceed
          </v-btn>
          <v-spacer></v-spacer>

          <v-btn
            color="green darken-1 white--text"
            @click="harmDialog = false; dialog = false;"
          >
            Back To Safety
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
// @ is an alias to /src
import { 
  mdiClose,
} from '@mdi/js'

export default {
  name: 'Home',
  components: {
  },
  data: () => ({
    dialog: false,
    understandDialog: false,
    beforeDialog: false,
    harmDialog: false,
    icons: {mdiClose}
  })
}
</script>
