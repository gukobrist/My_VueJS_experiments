<template>
  <div>
    <my-header :cartItemCount="cartItemCount"></my-header>
    <div class="row">
      <div class="col-md-10 col-md-offset-1">
        <div class="panel panel-info">
          <div class="panel-heading">Оформление заказа</div>
          <div class="panel-body">
            <div class="form-group">
              <div class="col-md-12">
                <h4><strong>Укажите данные для доставки</strong></h4>
              </div>
              <div class="form-group">
                <div class="col-md-6">
                  <strong>Фамилия:</strong>
                  <input v-model.trim="order.firstName" class="form-control" />
                </div>
                <div class="col-md-6">
                  <strong>Имя:</strong>
                  <input v-model.trim="order.lastName" class="form-control" />
                </div>
              </div>
              <div class="form-group">
                <div class="col-md-12"><strong>Адрес:</strong></div>
                <div class="col-md-12">
                  <input v-model.trim="order.address" class="form-control" />
                </div>
              </div>
              <div class="form-group">
                <div class="col-md-12"><strong>Город:</strong></div>
                <div class="col-md-12">
                  <input v-model.trim="order.city" class="form-control" />
                </div>
              </div>
              <div class="form-group">
                <div class="col-md-2">
                  <strong>Этаж:</strong>
                  <select v-model="order.floor" class="form-control">
                    <option disabled value=""></option>
                    <option v-for="(floor, key) in floors" v-bind:value="floor">
                      {{key}}
                    </option>
                  </select>
                </div>
              </div>
              <div class="form-group">
                <div class="col-md-6 col-md-offset-4">
                  <strong>Индекс:</strong>
                  <input v-model.number="order.zip"
                         class="form-control"
                         type="number"/>
                </div>
              </div>

              <div class="form-group">
                <div class="col-md-6 boxes">
                  <input type="checkbox"
                         id="gift" value="true"
                         v-bind:true-value="order.sendGift"
                         v-bind:false-value="order.dontSendGift"
                         v-model="order.gift">
                  <label for="gift">Упаковать?</label>
                </div>
              </div>
              <div class="form-group">
                <div class="col-md-6 boxes">
                  <input type="radio"
                         id="home"
                         v-bind:value="order.home"
                         v-model="order.method">
                  <label for="home">Домой</label>
                  <input type="radio"
                         id="business"
                         v-bind:value="order.business"
                         v-model="order.method">
                  <label for="business">На работу</label>
                </div>
              </div>
              <div class="form-group">
                <div class="col-md-6">
                  <button type="submit" class="btn btn-primary submit" v-on:click="submitForm">Оформить заказ</button>
                </div>
              </div>
              <div class="col-md-12 verify">
                  <pre>
                    Фамилия: {{order.firstName}}
                    Имя: {{order.lastName}}
                    Адрес: {{order.address}}
                    Город: {{order.city}}
                    Индекс: {{order.zip}}
                    Этаж: {{order.floor}}
                    Куда: {{order.method}}
                    Упаковать: {{order.gift}}
                  </pre>
              </div>
            </div>
          </div>
        </div>
      </div>
      </div>
    </div>
</template>

<script>
import MyHeader from "./Header";
export default {
  name: "Form",
  props: ['cartItemCount'],
  data () {
    return {
      floors: {
        1: 'Первый',
        2: 'Второй',
        3: 'Третий',
        4: 'Четвертый',
        5: 'Пятый'
      },
      order: {
        firstName: '',
        lastName: '',
        address: '',
        city: '',
        zip: '',
        floor: '',
        method: 'Домашний адрес',
        business: 'Рабочий адрес',
        home: 'Домашний адрес',
        gift:'Упаковать?',
        sendGift: 'Упаковать как подарок',
        dontSendGift: 'Не упаковывать как подарок'
      },
    }
  },
  components: {MyHeader},
  methods: {
    submitForm() {
      alert('Отправлено');
    }
  }
}
</script>

<style scoped>

</style>
