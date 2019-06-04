<template>
<v-app>
    <v-navigation-drawer 
      app 
      width="500px" 
      class="px-3" 
      v-model="drawer"
    >
      <v-layout justify-space-between column fill-height>
        <header>
          <v-list dense class="pt-0">
              <v-list-tile class="my-3">
                  <v-img 
                    src="fgklogo.png" 
                    max-width="90%" 
                    position="center" 
                    class="my-3" 
                  />
              </v-list-tile>
              <v-text-field 
                class="mx-3" 
                flat label="Search" 
                prepend-inner-icon="search" 
              />
              <v-list-tile 
                v-for="item in items" 
                :key="item.title" 
                class="my-3"
              >
                <v-list-tile-action>
                  <v-btn 
                    fab 
                    dark 
                    small 
                    color="red"
                  >
                    <v-icon color="white">{{ item.icon }}</v-icon>
                  </v-btn>
                </v-list-tile-action>
                <v-list-tile-content>
                    <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                </v-list-tile-content>
              </v-list-tile>
            </v-list>
        </header>
        <main 
          class="px-3"
        >
          <div class="content ml-5">
            <h2>Зимой дешевле</h2>
            <p>Закажи вагон зимой, чтобы <br/> сэкономить весной</p>
          </div>
          <div>
           <v-img
              src="image/pic.png" 
              width="100%"
              position="center" 
              class="my-2" 
            />
          </div>
          <div class="text-sm-center">
            <v-btn 
              class="white--text px-5"
              color="#EF3425"
            >
              Создать заявку
            </v-btn>
          </div>
        </main>
        <footer
          class="my-5 px-3"
        >
          <p>
            <v-btn 
              v-for="contact in contacts"
              :key="contact"
              outline 
              fab 
              color="#21212B"
            >
              <i 
                class="fa fa-2x"
                :class="contact"
                aria-hidden="true"
              ></i>
            </v-btn>
          </p>
          <div>&copy; {{ new Date().getFullYear() }} АО &laquo;Федеральная грузовая компания&raquo;</div>
        </footer>
      </v-layout>
    </v-navigation-drawer>
    <v-toolbar app>
      <v-toolbar-items class="hidden-sm-and-down">
          <v-btn 
            flat 
            @click="drawer = !drawer"
          >
            <span
              v-if="drawer"
            >Открыть&nbsp;</span>
            <span v-else>Cкрыть&nbsp;</span> 
            боковую панель
          </v-btn>
      </v-toolbar-items>
      <v-spacer></v-spacer>
      <v-toolbar-side-icon @click="drawer = !drawer">
      </v-toolbar-side-icon>
    </v-toolbar>

    <v-content>
      <v-container grid-list-md text-xs-center>
        <v-layout row wrap>
          <v-flex xs4>
            <app-form></app-form>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
</v-app>
</template>

<script>
  import appForm from './components/Form'

  export default {
    name: 'App',
    data() {
      return {
        drawer: true,
        items: [{
              title: 'Договоры',
              icon: 'assignment'
          },
          {
              title: 'Оперирование',
              icon: 'offline_pin'
          }
        ],
        contacts: [
          'fa-vk',
          'fa-facebook',
          'fa-instagram',
          'fab fa-youtube'
        ]
      }
    },
    components: {
      appForm
    }
  }
</script>

<style scoped>
  .v-btn {
    text-transform: none;
  }
</style>
