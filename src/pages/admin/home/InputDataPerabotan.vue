<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
  <q-page padding class="items-center-justify-center bg-grey-3">
    <q-card flat class="bg-white q-pa-md">
      <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-blue-grey-14">Tambah Data Barang</span>
      </span>
      <div class="q-pa-md">
        <q-form
          class="q-gutter-md"
        >

          <q-input
            label="Kode Barang"
            lazy-rules
            color="teal"
            v-model="kodebarang"
            :rules="[
           val => val !== null && val !== '' || 'Kode Barang Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="code"/>
            </template>
          </q-input>
          <q-input
            label="Nama Barang"
            lazy-rules
            color="teal"
            v-model="judulBuku"
            :rules="[
           val => val !== null && val !== '' || 'Nama Barang Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="list"/>
            </template>
          </q-input>
          <q-input
            label="Harga Barang"
            lazy-rules
            color="teal"
            v-model="hargabarang"
            :rules="[
           val => val !== null && val !== '' || 'harga Barang Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="attach_money"/>
            </template>
          </q-input>
          <q-input
            label="Jumlah Barang"
            lazy-rules
            color="teal"
            v-model="jumlahbarang"
            :rules="[
           val => val !== null && val !== '' || 'jumlah Barang Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="add_box"/>
            </template>
          </q-input>
          <q-input
            label="Tanggal Masuk Barang"
            lazy-rules
            color="teal"
            v-model="tanggalmasukbarang"
            :rules="[
           val => val !== null && val !== '' || 'tanggal masuk Barang Dibutuhkan'
           ]">
            <template v-slot:append>
              <q-icon name="calendar_today"/>
            </template>
          </q-input>

          <div>
            <q-btn
              unelevated
              icon="add"
              label="Tambah Data Barang"
              style="height: 50px"
              color="teal-6"/>
          </div>
        </q-form>
      </div>
    </q-card>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      namabarang: null,
      kodebarang: null,
      hargabarang: null,
      jumlahbarang: null,
      tanggalmasukbarang: null

    }
  }
}
</script>

<style scoped>

</style>
