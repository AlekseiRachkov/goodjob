<template lang="pug">
  .fish
    .container
      .main.noprint
        .main-item
          h3 Договор для техники
        .main-item(style="justify-content: flex-start")
          p Номер заказа
          form.main-item__form(@submit.prevent)
            input(v-alSum v-model="a1" required :class="{error: errorFunc(a1)}")
          p.ml-20 Номер телефона: +7
          form.main-item__form(@submit.prevent)
            input(v-phone v-model="a16" required :class="{error: errorFunc(a16)}")
        .main-item(style="justify-content: flex-start")
          p Введите дату
          form.main-item__form(@submit.prevent)
            input(v-dataNumer v-model="a2" required :class="{error: errorFunc(a2)}")
          select.ml-20(v-model="select" )
            option(disabled value="") Выберите торговый центр
            option(v-for="i of items" :key="i.id" :value="i") {{i.tg}}
        .main-item(style="justify-content: flex-start")
          p Фамилия:
          form.main-item__form(@submit.prevent)
            input(v-model="a3" required :class="{error: errorFunc(a3)}")
          p.ml-20 Имя:
          form.main-item__form(@submit.prevent)
            input(v-model="a4" required :class="{error: errorFunc(a4)}")
          p.ml-20 Отчество:
          form.main-item__form(@submit.prevent)
            input(v-model="a5" required :class="{error: errorFunc(a5)}")
        .main-item(style="justify-content: flex-start")
          p Паспорт: Серия
          form.main-item__form(@submit.prevent)
            input(v-Serius v-model="a6" required :class="{error: errorFunc(a6)}")
          p.ml-20 Номер
          form.main-item__form(@submit.prevent)
            input(v-Numer v-model="a7" required :class="{error: errorFunc(a7)}")
        .main-item(style="justify-content: flex-start")
          p Кем выдан
          form.main-item__form(@submit.prevent)
            input(v-model="a8" required :class="{error: errorFunc(a8)}")
          p.ml-20 Дата выдачи
          form.main-item__form(@submit.prevent)
            input(v-dataNumer v-model="a9" required :class="{error: errorFunc(a9)}")
        .main-item(style="justify-content: flex-start")
          p Регион:
          form.main-item__form(@submit.prevent)
            input(v-model="a10" required :class="{error: errorFunc(a10)}")
          p.ml-20 Район:
          form.main-item__form(@submit.prevent)
            input(v-model="a11" required)
          p.ml-20 Населенный пункт:
          form.main-item__form(@submit.prevent)
            input(v-model="a12" required :class="{error: errorFunc(a12)}")
        .main-item(style="justify-content: flex-start")
          p Улица:
          form.main-item__form(@submit.prevent)
            input(v-model="a13" required :class="{error: errorFunc(a13)}")
          p.ml-20 Дом:
          form.main-item__form(@submit.prevent)
            input(v-model="a14" required :class="{error: errorFunc(a14)}")
          p.ml-20 Квартира:
          form.main-item__form(@submit.prevent)
            input(v-model="a15" required)
        //- .main-item
        //-   h3 Адрес при получении у продавца
        //-   form.main-item__form(@submit.prevent)
        //-     input(v-model="a17" required)
        .main-item(style="justify-content: flex-start")
          h3 Данные для доставки
        .main-item(style="justify-content: flex-start")
          h3 Выберите при передача Товара в месте нахождения Продавца
          input.radio(type="radio" value="1" v-model="user")
        .main-item(style="justify-content: flex-start")
          h3 Выберите при доставке до двери подъезда
          input.radio(type="radio" value="2" v-model="user")
        .main-item(style="justify-content: flex-start")
          h3 Выберите при доставке до двери квартиры
          input.radio(type="radio" value="3" v-model="user")
        .main-item(style="justify-content: flex-start")
          p Регион:
          form.main-item__form(@submit.prevent)
            input(v-model="a18" required :class="{error: errorFunc(a18)}")
          p.ml-20 Район:
          form.main-item__form(@submit.prevent)
            input(v-model="a19" required)
          p.ml-20 Населенный пункт:
          form.main-item__form(@submit.prevent)
            input(v-model="a20" required :class="{error: errorFunc(a20)}")
        .main-item(style="justify-content: flex-start" )
          p Улица:
          form.main-item__form(@submit.prevent)
            input(v-model="a21" required :class="{error: errorFunc(a21)}")
          p.ml-20 Дом:
          form.main-item__form(@submit.prevent)
            input(v-model="a22" required :class="{error: errorFunc(a22)}")
          p.ml-20 Квартира:
          form.main-item__form(@submit.prevent)
            input(v-model="a23" required)
        .main-item(style="justify-content: flex-start")
          h3 Техника
        .main-item(v-for="(item, i) in count" :key="item.id" style="justify-content: space-between;")
          form
            p Наименование (включая артикул)
            input(v-model.lazy="use[i]" :oops="l()" )
          form.ml-20
            p Количество
            input(v-model.lazy="use1[i]" :oops="l()" v-alSum)
          form.ml-20
            p Ед.изм.
            input(v-model.lazy="use2[i]" :oops="l()" )
          form.ml-20
            p Цена
            input(v-model.lazy="use3[i]" :oops="l()" v-alSum)
        .main-item
          button.btn(@click="count += 1") Добавить ещё технику
        .main-item
          p Аванс:
          form.main-item__form(@submit.prevent)
            input(v-model="a24" required :class="{error: errorFunc(a24)}" v-alSum)
        .main-item
          input.noprint.btn(v-if="fantom(visible)" @click="lock = !lock" type="button" value="Печать")
      .main.fish-print(v-if="lock" :lockss="locks" )
        h2 Договор № {{s[24]}}/{{s[1]}}
        .main-item
          h3 купли-продажи бытовой техники
        .main-item.sb
          p г. Ульяновск
          p {{s[2]}}
        .main-item.colum
          p <b>ООО Какое нибудь</b>, в лице {{select.nameS}} , с одной стороны
          p {{ s[3] }} {{ s[4] }} {{ s[5] }}
          p паспорт  серия {{s[6]}} № {{s[7]}}
          p выдан (кем и когда): {{s[8]}} от {{s[9]}}
          p проживающий  по адресу: {{s[10] + ', ' + s[12] + ', ' + s[11] + ', ' + s[13] + ' ' + s[14] + ' ' + s[15]}}
          p Именуемый(ая) в дальнейшем <b>«Покупатель»</b>, с другой стороны, именуемые совместно Стороны, заключили настоящий договор о нижеследующем:
          h3 2.	Предмет договора
          p Продавец обязуется передать в собственность Покупателя:
        .main-item
          table.table(border='1' cellspacing="0" cellpadding="2")
            tr
              td № п\п
              td Наименование (включая артикул)
              td Количество
              td Ед.изм.
              td Цена
            tr(v-for="(item, i) of mas" :key="item.id")
              td {{i + 1}}
              td {{item.name}}
              td {{item.num}}
              td {{item.ci}}
              td {{spaceData(String(item.price))}}
        .main-item(style="margin-top: -5px; justify-content: flex-end;")
          table.table-all(border='1' cellspacing="0" cellpadding="2")
            tr
              td Итого количество: {{spaceData(String(sumMas[0]))}} ед.
              td Итого сумма: {{spaceData(String(sumMas[1]))}}
        .main-item.colum
          p далее Товар, а Покупатель принять и оплатить его стоимость на условиях настоящего договора
          h3 3. Порядок поставки
          p(v-if="user == 1") Передача Товара в месте нахождения Продавца по адресу: {{s[18] + ', ' + s[20] + ', ' + s[19] + ', ' + s[21] + ' ' + s[22] + ' ' + s[23]}}
          p(v-if="user == 2") Доставка Товара до двери подъезда по адресу: {{s[18] + ', ' + s[20] + ', ' + s[19] + ', ' + s[21] + ' ' + s[22] + ' ' + s[23]}}
          p(v-if="user == 3") Доставка Товара до двери квартиры: {{s[18] + ', ' + s[20] + ', ' + s[19] + ', ' + s[21] + ' ' + s[22] + ' ' + s[23]}}
          p 4. Стоимость, сроки и порядок оплаты Товара: Аванс: {{spaceData(String(Number(s[26])))}} руб. доплата до момента отгрузки {{spaceData(String(Number(sumMas[1]) - Number(s[26])))}} руб.
          p 5.	Гарантия исчисляется с даты получения Товара. Срок гарантии указывается в документах изготовителя, если гарантийный срок не указан, то на такой товар гарантийный срок не может превышать шести месяцев  исчисляя с даты получения Товара. Условия гарантии определяются изготовителем. При их отсутствии гарантийным не признаются недостатки, связанные с действиями Покупателя повлиявшие на возникновение дефекта и т.д.
          p 6.	Подтверждением получения Товара является товарная накладная или иной документ подтверждающей его получения. Подпись Покупателя в данном документе подтверждает получение Товара и его соответствие количеству, качеству, количеству, комплектности, комплекту. После подписания передаточного документа (товарной накладной и т.д.) Покупатель не имеет право на предъявление претензий по состоянию внешнего вида, количеству, комплекту, комплектности, качеству.
          h3 6.	Реквизиты сторон
        .main-item
          .main-item-block
            p <b><i>Заказчик:</i></b>
          .main-item-block
            p <b><i>Продавец:</i></b>
        .main-item
          table(border='1' cellspacing="0" cellpadding="2")
            tr
              td Ф. {{s[3]}}
              td ООО Какое нибудь
            tr
              td И. {{s[4]}}
              td ИНН -------- КПП ---------
            tr
              td О. {{s[5]}}
              td адрес и телефон
            tr
              td Паспорт серия {{s[6]}} № {{s[7]}} <br> Когда выдан {{s[9]}} <br> Кем выдан {{s[8]}}
              td сайт
            tr
              td {{s[10] + ', ' + s[12] + ', ' + s[11] + ', ' + s[13] + ' ' + s[14] + ' ' + s[15]}}
              td E-mail: {{select.email}}
            tr
              td Тел.: +7 {{s[16]}}
              td р/с ----------------
            tr
              td
              td Отделение
            tr
              td
              td к/с ---------------------
            tr
              td
              td БИК ----------------------
        .main-item
          .main-item-block
            p <b><i>Заказчик:</i></b>
          .main-item-block
            p <b><i>Продавец:</i></b>
        .main-item
          .main-item-block
            p <b><i>____________________/{{s[3]}} {{s[4]}} {{s[5]}}/</i></b>
          .main-item-block
            p <b><i>____________________/{{select.name}}/:</i></b>
</template>

<script>
let l = [{
        tg: 'Салон 1',
        name: 'Управляющий такой-то',
        nameS: 'Управляющий действующий',
        email: 'майл'
      },
      {
        tg: 'Салон 2',
        name: 'Управляющий такой-то2',
        nameS: 'Управляющий действующий2',
        email: 'майл2'
      },
      {
        tg: 'Салон 3',
        name: 'Управляющий такой-то3',
        nameS: 'Управляющий действующий3',
        email: 'майл3'
      }
      ]

export default {
  props: ['li'],
  name: 'urtehn',
  data () {
    return {
      select: this.lost(this.li),
      items: l,
      visible: true,
      lock: false,
      user: 1,
      a1: '', // номер заказа
      a2: '', // дата заказа
      a3: '', // фамилия
      a4: '', // имя
      a5: '', // отчество
      a6: '', // серия
      a7: '', // номер
      a8: '', // кем выдан
      a9: '', // дата выдачи
      a10: 'Ульяновская область', // регион
      a11: '', // район
      a12: 'г. Ульяновск', // Населенный пункт
      a13: '', // Улица
      a14: '', // Дом
      a15: '', // Квартира
      a16: '', //номер телефона
      a17: '', //Адрес при получении у продавца
      a18: 'Ульяновская область', // регион
      a19: '', // район
      a20: 'г. Ульяновск', // Населенный пункт
      a21: '', // Улица
      a22: '', // Дом
      a23: '', // Квартира
      a24: '', //аванс
      count: 1, //счетчик для кнопки
      use: this.l(),
      use1: this.l(),
      use2: this.l(),
      use3: this.l()
    }
  },
  computed: {
    mas() {
      let c = this.count,
        a1 = this.use,
        a2 = this.use1,
        a3 = this.use2,
        a4 = this.use3,
        arr = []

      for (let j = 0; j < c; j++) {
        if (typeof a4[j] === 'undefined') {
          a4[j] = 0
        }
        if (typeof a2[j] === 'undefined') {
          a2[j] = 0
        }

        const element = j;
        let b = {name: a1[j],
          num: a2[j],
          ci: a3[j],
          price: a2[j] == 0? a4[j]: a4[j]*a2[j]
        }

        arr.push(b)
      }

      return arr
    },
    locks() {
      if (this.lock == true) {
        setTimeout(() => window.print(), 1500);
        return setTimeout(() => this.lock=false, 3500);
      }
    },
    s () {
      let a0 = '',
        a1 = this.a1,
        a2 = this.a2,
        a3 = this.a3,
        a4 = this.a4,
        a5 = this.a5,
        a6 = this.a6,
        a7 = this.a7,
        a8 = this.a8,
        a9 = this.a9,
        a10 = this.a10,
        a11 = this.a11,
        a12 = this.a12,
        a13 = this.a13,
        a14 = this.a14,
        a15 = this.a15,
        a16 = this.a16,
        a17 = this.a17,
        a18 = this.a18,
        a19 = this.a19,
        a20 = this.a20,
        a21 = this.a21,
        a22 = this.a22,
        a23 = this.a23,
        a24 = this.select.tg, //Выбор торгового центра
        a25 = this.select.name,
        a26 = this.a24,
        s = [a0,a1,a2,a3,a4,a5,a6,a7,a8,a9,a10,a11,a12,a13,a14,a15,a16,a17,a18,a19,a20,a21,a22,a23,a24,a25,a26]

        return s
    },
    sumMas() {
      let m = this.mas,
        arr1 = [],
        arr2 = []

      for (let index = 0; index < m.length; index++) {
        const element = m[index];
        // if (typeof element.num === 'undefined') {
        //   element.num = 0
        // }

        // if (typeof element.price === 'undefined') {
        //   element.price = 0
        // }

        arr1.push(element.num)
        arr2.push(element.price)
      }

      let col1 = arr1.reduce((x, a)=> {

        return x + Number(a)
      }, 0)

      let col2 = arr2.reduce((x, a)=> {

        return x + Number(a)
      }, 0)

      let allElem = []

      allElem.push(col1, col2)

      return allElem
    }
  },
  methods: {
    spaceData(e) {
      return e===""? "": e.replace(/(\d)(?=(\d\d\d)+([^\d]|$))/g, '$1 ')
    },
    l() {
      let c = this.count,
        arr = []

        for (let i = 0; i < c; i++) {
          const element = i;

          arr.push(element)
        }

      return arr
    },
    lost(e) {
      let t = l

      if (e == 11) {
          return t[0]
      } else if (e == 12) {
          return t[1]
      } else if (e == 13) {
          return t[2]
      } else {
          return ''
      }
    },
    fantom(e) {
      let s = this.s

      if (s[1] != '' && s[2] != '' && s[3] != '' && s[4] != '' && s[5] != '' && s[6] != '' && s[7] != '' && s[8] != '' && s[9] != '' && s[10] != '' && s[12] != '' && s[13] != '' && s[14] != '' && s[16] != '' && s[18] != '' && s[20] != '' && s[21] != '' && s[22] != '' && (s[24] != '' && typeof s[24] !='undefined') && s[26] != '') {
        return e
      } else {
        return !e
      }
    },
    errorFunc(e) {
      if (e != '') {
        return false
      } else {
        return true
      }
    }
  },
  directives: {
    Serius: {
      bind(el) {
        el.oninput = function(e) {
          if (!e.isTrusted) {
            return;
          }

          let x = this.value.replace(/\D/g, "").match(/(\d{0,2})(\d{0,2})(\d{0,3})/);

          this.value = !x[2]? x[1]: x[1] + " " + x[2]
          el.dispatchEvent(new Event("input"));
        };
      }
    },
    Numer: {
        bind(el) {
          el.oninput = function(e) {
            if (!e.isTrusted) {
              return;
            }

            let x = this.value.replace(/\D/g, "").match(/(\d{0,3})(\d{0,3})/);

            this.value = !x[2]? x[1]: x[1] + " " + x[2]
            el.dispatchEvent(new Event("input"));
          };
        }
      },
    dataNumer: {
      bind(el) {
        el.oninput = function(e) {
          if (!e.isTrusted) {
            return;
          }

          let x = this.value.replace(/\D/g, "").match(/(\d{0,2})(\d{0,2})(\d{0,4})/);

          this.value = !x[2]? x[1]: x[1] + "." + x[2] + (x[3] ? "." + x[3] : "");
          el.dispatchEvent(new Event("input"));
        };
      }
    },
    phone: {
      bind(el) {
        el.oninput = function(e) {
          if (!e.isTrusted) {
            return;
          }

          let x = this.value.replace(/\D/g, "").match(/(\d{0,3})(\d{0,3})(\d{0,2})(\d{0,2})/);
          this.value =  !x[2]? x[1]: "(" + x[1] + ") " + x[2] + (x[3] ? "-" + x[3] : "") + (x[4] ? " " + x[4] : "");
          el.dispatchEvent(new Event("input"));
        };
      }
    },
    alSum: {
      bind(el) {
        el.oninput = function(e) {
          if (!e.isTrusted) {
            return;
          }

          let x = this.value.replace(/\D/g, "").match(/(\d{0,9})/);
          this.value =  !x[2]? x[1]: x[1]
          el.dispatchEvent(new Event("input"));
        };
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="stylus">
@import '../styles/smart-grid'

.radio
  margin-left 20px

.table
  mixSize(100%)
  & th, td
    $listTable = 10% 60% 10% 10% 10%
    for item, index in $listTable
      &:nth-child({index + 1})
        mixSize(item)
  &-all
    mixSize(50%)
</style>
