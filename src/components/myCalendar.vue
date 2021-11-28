<template>
  <div class="container">
    <div ref="entireCalendar" class="calendar">
      <transition
        enter-active-class="animated fadeInRight"
        leave-active-class="animated fadeOutLeft"
      >
        <div v-if="step === 0" class="calendar-block date_and_time">
          <div class="row">
            <div class="col m4 menu">
              <!-- Menu -->
              <h3>Онлайн запись</h3>
              <ul>
                <li>
                  <img src="../assets/calendar.png" alt="" />
                  <p>Дата и время</p>
                </li>

                <li>
                  <img src="../assets/language.png" alt="" />
                  <p>Язык</p>
                </li>

                <li>
                  <img src="../assets/presentation1.png" alt="" />
                  <p>Вид занятия</p>
                </li>
                <li>
                  <img src="../assets/contact-mail.png" alt="" />
                  <p>Контакты</p>
                </li>
              </ul>
            </div>
            <div class="col m8 right-panel">
              <h2>Выберите дату и время</h2>
              <input
                ref="calendar"
                type="text"
                class="datepicker"
                placeholder="Выберите дату"
                required
              />
              <input
                type="text"
                class="timepicker"
                placeholder="Выберите время"
                required
              />
              <div class="forbtn">
                <my-btn @click="next" class="btn-next">Далее</my-btn>
              </div>
            </div>
          </div>
        </div>
      </transition>

      <transition
        enter-active-class="animated fadeInRight"
        leave-active-class="animated fadeOutLeft"
      >
        <div v-if="step === 1" class="calendar-block language">
          <div class="row">
            <div class="col m4 menu">
              <!-- Menu -->
              <h3>Онлайн запись</h3>
              <ul>
                <li>
                  <img src="../assets/calendar-done1.png" alt="" />
                  <p>Дата и время</p>
                </li>

                <li>
                  <img src="../assets/language.png" alt="" />
                  <p>Язык</p>
                </li>

                <li>
                  <img src="../assets/presentation1.png" alt="" />
                  <p>Вид занятия</p>
                </li>
                <li>
                  <img src="../assets/contact-mail.png" alt="" />
                  <p>Контакты</p>
                </li>
              </ul>
            </div>
            <div class="col m8 right-panel">
              <h2>Выберите язык</h2>
              <list-of-languages />
              <div class="forbtn">
                <div class="btns">
                  <my-btn @click="prev" class="btn-prev">Назад</my-btn>
                  <my-btn @click="next" class="btn-next">Далее</my-btn>
                </div>
              </div>
            </div>
          </div>
        </div>
      </transition>

      <transition
        enter-active-class="animated fadeInRight"
        leave-active-class="animated fadeOutLeft"
      >
        <div v-if="step === 2" class="calendar-block kinds">
          <div class="row">
            <div class="col m4 menu">
              <!-- Menu -->
              <h3>Онлайн запись</h3>
              <ul>
                <li>
                  <img src="../assets/calendar-done1.png" alt="" />
                  <p>Дата и время</p>
                </li>

                <li>
                  <img src="../assets/language.png" alt="" />
                  <p>Язык</p>
                </li>

                <li>
                  <img src="../assets/presentation1.png" alt="" />
                  <p>Вид занятия</p>
                </li>
                <li>
                  <img src="../assets/contact-mail.png" alt="" />
                  <p>Контакты</p>
                </li>
              </ul>
            </div>
            <div class="col m8 right-panel">
              <h2>Выберите вид занятия</h2>
              <div class="row">
                <div class="col m4">
                  <div class="block">
                    <p class="kind">
                      <span
                        @click="kind = 'distant'"
                        :class="{ kindchecked: kind === 'distant' }"
                        >Дистанионно</span
                      >
                    </p>
                  </div>
                </div>
                <div class="col m4">
                  <div class="block">
                    <p class="kind">
                      <span
                        @click="kind = 'ochno'"
                        :class="{ kindchecked: kind === 'ochno' }"
                        >Очно</span
                      >
                    </p>
                  </div>
                </div>
              </div>
              <div class="forbtn">
                <div class="btns">
                  <my-btn @click="prev" class="btn-prev">Назад</my-btn>
                  <my-btn @click="next" class="btn-next">Далее</my-btn>
                </div>
              </div>
            </div>
          </div>
        </div>
      </transition>

      <transition
        enter-active-class="animated fadeInRight"
        leave-active-class="animated fadeOutLeft"
      >
        <div v-if="step === 3" class="calendar-block contacts">
          <div class="row">
            <div class="col m4 menu">
              <!-- Menu -->
              <h3>Онлайн запись</h3>
              <ul>
                <li>
                  <img src="../assets/calendar-done1.png" alt="" />
                  <p>Дата и время</p>
                </li>

                <li>
                  <img src="../assets/language.png" alt="" />
                  <p>Язык</p>
                </li>

                <li>
                  <img src="../assets/presentation1.png" alt="" />
                  <p>Вид занятия</p>
                </li>
                <li>
                  <img src="../assets/contact-mail.png" alt="" />
                  <p>Контакты</p>
                </li>
              </ul>
            </div>
            <div class="col m8 right-panel">
              <h2>Укажите имя и телефон</h2>
              <div class="row">
                <div class="col m12">
                  <input
                    class="contacts-input"
                    type="text"
                    placeholder="Ваше имя"
                  />
                </div>
                <div class="col m12">
                  <input
                    class="contacts-input"
                    type="text"
                    placeholder="Телефон"
                  />
                </div>
              </div>
              <div class="forbtn">
                <div class="btns">
                  <my-btn @click="prev" class="btn-prev">Назад</my-btn>
                  <my-btn @click="next" class="btn-next">Далее</my-btn>
                </div>
              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>

<script>
import myBtn from "./myBtn.vue";
import listOfLanguages from "./listOfLanguages.vue";
import M from "../../node_modules/materialize-css";

export default {
  components: {
    myBtn,
    listOfLanguages,
  },
  data() {
    return {
      step: 0,
      kind: "",
    };
  },
  methods: {
    next() {
      this.step++;
    },
    prev() {
      this.step--;
    },
    isVisible() {
      let coords = this.$refs.entireCalendar.getBoundingClientRect();
      let windowHeight = document.documentElement.clientHeight;
      let topVisible = windowHeight - coords.top;

      return [coords, windowHeight, topVisible];
    },
  },
  mounted() {
    document.addEventListener("scroll", () => {
      console.log(this.isVisible());
    });
    document.addEventListener("DOMContentLoaded", () => {
      var elem = this.$refs.calendar;
      M.Datepicker.init(elem, {
        firstDay: 1,
        i18n: {
          cancel: "Закрыть",
          done: "Ок",
          months: [
            "Январь",
            "Февраль",
            "Март",
            "Апрель",
            "май",
            "Июнь",
            "Июль",
            "Август",
            "Сентябрь",
            "Октябрь",
            "Ноябрь",
            "Декабрь",
          ],
          monthsShort: [
            "Янв",
            "Фев",
            "Мар",
            "Апр",
            "Мая",
            "Июня",
            "Июля",
            "Авг",
            "Сен",
            "Окт",
            "Ноя",
            "Дек",
          ],
          weekdays: [
            "Воскресенье",
            "Понедельник",
            "Вторник",
            "Среда",
            "Четверг",
            "Пятница",
            "Суббота",
          ],
          weekdaysShort: ["Вс", "Пн", "Вт", "Ср", "Чт", "Пт", "Сб"],
          weekdaysAbbrev: ["Вс", "Пн", "Вт", "Ср", "Чт", "Пт", "Сб"],
        },
      });
    });
  },
};
</script>

<style lang="less" scoped>
.calendar {
  position: relative;
  height: 550px;
  margin-bottom: 200px;
  &-block {
    height: 100%;
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
  }
}
span {
  position: relative;
  &::after {
    content: "";
    height: 5px;
    width: 100%;
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #f17f77;
    border-radius: 50px;
    opacity: 0;
  }
  &:hover {
    cursor: pointer;
  }
  &:hover::after {
    opacity: 1;
  }
}
.kindchecked {
  position: relative;
  &::after {
    content: "";
    height: 5px;
    width: 100%;
    position: absolute;
    top: 100%;
    left: 0;
    background-color: #f17f77;
    border-radius: 50px;
    opacity: 1 !important;
  }
}
.kind {
  color: #000;
}
input {
  padding: 10px !important;
}
img {
  width: 35px;
  height: 35px;
}
.row {
  height: 100% !important;
}
.menu {
  background-color: #f17f77;
  height: 100%;
}
ul {
  display: flex;
  flex-direction: column;
  align-items: center;
}
li {
  min-width: 200px;
  display: flex;
  align-items: center;
  &:not(:first-child) {
    margin-top: 20px;
  }
}
p {
  font-weight: 500;
  font-size: 18px;
  color: #fff;
  margin: 0 20px;
}
h3,
h2 {
  margin: 0;
  text-align: center;
  margin: 60px 0;
  font-size: 35px;
  color: #fff;
  font-weight: 900;
}
h2 {
  color: #000 !important;
  text-align: left;
}
.right-panel {
  padding: 0 60px 0 40px !important;
  display: flex;
  flex-direction: column;
  height: 100%;
  border: 1px solid #f17f77;
}
.btn {
  &-next {
    width: 200px;
    position: absolute;
    bottom: 100px;
    right: -20px;
  }
  &-prev {
    width: 200px;
    position: absolute;
    bottom: 100px;
    left: 0;
  }
}
.forbtn {
  height: 100%;
  flex-grow: 1;
  position: relative;
}
.btns {
  display: flex;
}
.contacts-input {
  &:focus {
    border-bottom: 1px solid #f17f77 !important;
    box-shadow: 0 1px 0 0 #f17f77 !important;
  }
}
</style>

<style lang="less">
.datepicker-date-display,
.timepicker-digital-display {
  background-color: #f17f77 !important;
}
.is-selected {
  background-color: #f17f77 !important;
}
.datepicker-table td.is-today,
.timepicker-close {
  color: #f17f77 !important;
}
.datepicker-table td.is-selected {
  color: #fff !important;
}
.month-prev,
.month-next {
  &:focus {
    background-color: #f17f77 !important;
  }
}
.datepicker-cancel,
.datepicker-clear,
.datepicker-today,
.datepicker-done {
  color: #f17f77 !important;
}
.timepicker,
.datepicker {
  &:focus {
    border-bottom: 1px solid #f17f77 !important;
    box-shadow: 0 1px 0 0 #ccb9b7 !important;
  }
}
</style>
