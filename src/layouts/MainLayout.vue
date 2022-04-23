<template>
  <q-layout view="lHh Lpr lFf">
    <q-header reveal class="bg-primary text-white" height-hint="98">
      <q-toolbar class="bg-blue-grey text-white shadow-2 rounded-borders">
        <img
          :src="require('../assets/car-svgrepo-com.svg')"
          style="height: 40px"
          alt="ремонт машин"
        />
        <q-btn flat label="ООО Авто-механика" />
        <q-space />

        <!--
          notice shrink property since we are placing it
          as child of QToolbar
        -->
        <div>
          <div style="font-size: 20px">Понедельник-пятница с 8:00 до 17:00</div>
          <div style="font-size: 20px">Суббота с 8:00 до 14:00</div>
        </div>
      </q-toolbar>
    </q-header>

    <!--    <q-page-container>
      <router-view />
    </q-page-container>-->
    <div
      style="display: flex; justify-content: flex-start; align-items: center"
    >
      <div class="q-pa-md" style="width: 45%">
        <form class="q-gutter-md" ref="form" @submit.prevent="sendEmail">
          <h2>Заказать звонок</h2>

          <q-input
            ref="nameRef"
            filled
            v-model="form.name"
            label="Ваше имя *"
            hint="Name and surname"
            lazy-rules
            name="name"
            :rules="[
              (val) => (val && val.length > 0) || 'Как к вам обращаться?',
            ]"
          />

          <q-input
            v-model="form.tel"
            filled
            type="tel"
            hint="Telephone number"
            label=" 071*******"
            name="tel"
            :rules="[
              (val) =>
                (val !== null && val !== '') || 'Пожалуйста, введите телефон',
              (val) =>
                (val.length > 6 && val.length < 16) ||
                'Пожалуйста, введите реальный номер телефон',
            ]"
          />

          <q-input
            v-model="form.email"
            filled
            type="email"
            hint="Email"
            label="@gmail.com"
            name="email"
          />

          <q-input
            v-model="form.text"
            filled
            type="textarea"
            hint="Опишите модель/проблему вашей машины"
            name="message"
          />

          <q-btn
            flat
            color="primary"
            label="Отправить"
            type="submit"
            value="Send"
          >
            <q-tooltip> Мы с вами свяжемся </q-tooltip>
          </q-btn>
        </form>
      </div>
      <div class="row justify-between" style="width: 55%">
        <q-parallax
          style="height: 800px"
          :src="require('../assets/man-362150_1920.jpg')"
          alt="ремонт машин"
        >
          <h1 style="color: white; font-size: 56px">АВТО-МЕХАНИКА</h1>
        </q-parallax>
      </div>
    </div>

    <div
      style="
        min-height: 600px;
        background-color: #1d1d1d;
        width: 100%;
        text-align: center;
        padding-top: 20px;
      "
    >
      <h2 style="color: white; margin: 0px 0px 0px 0px">
        Какие виды работ мы выполняем
      </h2>

      <div
        style="display: flex; justify-content: space-between; flex-wrap: wrap"
      >
        <q-card
          class="my-card"
          style="
            width: 25%;
            max-height: 50%;
            background-color: white;
            margin: 10% auto;
            min-width: 250px;
          "
        >
          <q-img
            :src="require('../assets/egor-myznik-C4dFQqNVt8g-unsplash.jpg')"
            alt="ремонт машин"
          >
            <div class="absolute-bottom text-h6">Ремонт Ходовой части</div>
          </q-img>

          <q-card-section style="background-color: white">
            Мы сделаем качественную диагностику, разборку-сборку и замену
            запчастей ходовой части
          </q-card-section>
        </q-card>

        <q-card
          class="my-card"
          style="
            width: 25%;
            height: 50%;
            background-color: white;
            margin: 10% auto;
            min-width: 250px;
          "
        >
          <q-img
            :src="
              require('../assets/benjamin-brunner-K3cjUOMmMhc-unsplash.jpg')
            "
            alt="ремонт машин"
          >
            <div class="absolute-bottom text-h6">Шиономонтаж</div>
          </q-img>

          <q-card-section style="background-color: white">
            Произведем шиономнтаж, балансировку, прокатку дисков
          </q-card-section>
        </q-card>

        <q-card
          class="my-card"
          style="
            width: 25%;
            height: 50%;
            background-color: white;
            min-width: 250px;
            margin: 10% auto;
          "
        >
          <q-img
            :src="require('../assets/kenny-eliason-ZSz1m4JPDqU-unsplash.jpg')"
            alt="ремонт машин"
          >
            <div class="absolute-bottom text-h6">Развал схождение</div>
          </q-img>

          <q-card-section style="background-color: white">
            Развал схождение на все виды легковых машин и микроавтобусов
          </q-card-section>
        </q-card>
      </div>
    </div>
    <div style="display: flex; height: 500px">
      <div style="width: 40%">
        <q-parallax>
          <template v-slot:media>
            <img
              :src="require('../assets/winter-5814578_1920.jpg')"
              style="height: 200%"
              alt="ремонт машин"
            />
          </template>

          <template v-slot:content="scope">
            <div
              class="absolute column items-center"
              :style="{
                top: scope.percentScrolled * 60 + '%',
                left: 0,
                right: 0,
              }"
            >
              <div class="text-h3 text-white text-center mdi-size-l">
                Надежность и качество
              </div>
            </div>
          </template>
        </q-parallax>
      </div>
      <div class="q-pa-md" style="margin-bottom: 0px; width: 60%">
        <q-table
          title="Весь список наших услуг/цена"
          :rows="rows"
          :columns="columns"
          row-key="name"
          hide-header
          hide-bottom
          dark
        />
      </div>
    </div>

    <iframe
      style="width: 100%"
      src="https://yandex.ru/map-widget/v1/?um=constructor%3A5c2e110965d2e06bf2e16a270d726d47081d65081f567227eac8d6dd34ceef04&amp;source=constructor"
      width="964"
      height="512"
      frameborder="0"
    ></iframe>

    <q-footer reveal elevated class="bg-blue-grey" style="margin-top: 50px">
      <q-toolbar style="display: flex; justify-content: space-between">
        <div style="display: flex">
          <img
            :src="require('../assets/car-svgrepo-com.svg')"
            alt="ремонт машин"
            style="height: 40px"
          />
          <q-toolbar>Наш адрес: ДНР, Макеевка, ул. Димитрова, д. 70</q-toolbar>
        </div>
        <div>
          Связь с нами: <br />Телефон:
          <strong style="font-size: 18px">071 401 4146</strong> <br />Почта:
          <strong>Pustobaev_a.a@Outlook.com </strong>
        </div>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import emailjs from "@emailjs/browser";
import { defineComponent, ref } from "vue";

const columns = [
  {
    name: "name",
    required: true,
    label: "Dessert (100g serving)",
    align: "left",
    field: (row) => row.name,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "Цена",
    align: "center",
    label: "price",
    field: "price",
    sortable: true,
  },
];

const rows = [
  {
    name: "Диагностика ходовой",
    price: "300р",
  },
  {
    name: "Замена наконечников/саленблоков/стоек армотизаторов(| сторона)",
    price: "от 1500р",
  },
  {
    name: "Развал-схождение",
    price: "от 1000р",
  },
  {
    name: "Шиномонтаж(4 колеса)",
    price: "от 700р",
  },
  {
    name: "Ремонт ДВС",
    price: "от 10 000р",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {},
  data() {
    return {
      form: {
        name: "",
        tel: "",
        email: "",
        text: "",
      },
    };
  },
  setup() {
    const leftDrawerOpen = ref(false);

    return {
      leftDrawerOpen,
      columns,
      rows,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
  methods: {
    sendEmail() {
      emailjs
        .sendForm(
          "service_b5by3fb",
          "template_s5svgw7",
          this.$refs.form,
          "kK37tPOxTXF9v9DMF"
        )
        .then(
          (result) => {
            console.log("SUCCESS!", result.text);
          },
          (error) => {
            console.log("FAILED...", error.text);
          }
        );
    },
  },
});
</script>
