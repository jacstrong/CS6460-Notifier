<template>
  <v-container fluid>
    <v-row
      row
      wrap
      align="center"
      justify="center"
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
                  @click.stop="dialog = true"
                >
                  Advanced
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
        <v-card-title class="headline">Help me make a decision.</v-card-title>

        <v-card-text>
          <v-btn
            color="red darken-1"
            text
            @click="understandDialog = true"
          >
            I do not understand this warning
          </v-btn>
        </v-card-text>

        <v-card-text>
          <v-btn
            color="red darken-1"
            text
            @click="dialog = false"
          >
            I have used this type of app befor without any problem
          </v-btn>
        </v-card-text>
        <v-card-text>
          <v-btn
            color="red darken-1"
            text
            @click="dialog = false"
          >
            I do not think this app would do any harm to my computer
          </v-btn>
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>


          <v-btn
            color="green darken-1"
            
            @click="dialog = false"
          >
            Back To Safety
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-dialog
      v-model="understandDialog"
      fullscreen
    >
      <!-- max-width="600" -->
      <v-card tile>
        <v-img src="../assets/bad-guy.png">
        </v-img>
        <v-card-title class="headline">I do not understand</v-card-title>

        <v-card-text>
          Think of a stranger <strong class="red--text">(the untrusted app)</strong> trying to gain access to your house
          <strong class="red--text">(your device)</strong>.
          Would you prefer handing over the key (allow permission to make changes to your device - 
          <a class="black--text" @click="understandDialog = false; dialog = false">Proceed Anyway</a>)
          or 
          stop him right away (block permission - <a class="black--text" @click="understandDialog = false; dialog = false">Back to Safety</a>)?          
        </v-card-text>

        <v-card-actions>
          <v-spacer></v-spacer>


          <!-- <v-btn
            color="green darken-1"
            
            @click="understandDialog = false"
          >
            Back To Safety
          </v-btn> -->
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
    icons: {mdiClose}
  })
}
</script>
