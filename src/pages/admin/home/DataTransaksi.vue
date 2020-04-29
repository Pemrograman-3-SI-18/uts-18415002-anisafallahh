<template>
  <q-page>
    <div class="q-pa-md">
      <q-table
        title="Treats"
        :data="data"
        :columns="columns"
        row-key="id"
        :filter="filter"
        :loading="loading"
      >

        <template v-slot:top>
          <span class="text-h5 text-weight-light q-pa-md">
        <span class="text-blue-grey-14">Tambah Data Transaksi</span>
      </span>
          <!--          <q-btn class="q-ml-sm" color="primary" :disable="loading" label="Remove row" @click="removeRow" />-->
          <q-space />
          <q-input borderless dense debounce="300" color="primary" v-model="filter">
            <template v-slot:append>
              <q-icon name="search" />
            </template>
          </q-input>
        </template>

      </q-table>
    </div>
  </q-page>
</template>

<script>
export default {
  data () {
    return {
      loading: false,
      filter: '',
      rowCount: 10,
      columns: [
        {
          name: 'desc',
          required: true,
          label: 'Kode Transaksi',
          align: 'left',
          field: row => row.KodeTransaksi,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'namapembeli', align: 'center', label: 'Nama Pembeli', field: 'namapembeli', sortable: true },
        { name: 'namabarang', align: 'center', label: 'Nama Barang', field: 'namabarang', sortable: true },
        { name: 'hargabarang', label: 'Harga Barang', align: 'center', field: 'hargabarang' },
        { name: 'jumlahbarang', label: 'Jumlah Barang', align: 'center', field: 'jumlahbarang' },
        { name: 'Total', label: 'Total', align: 'center', field: 'total' }

      ],
      data: [
        {
          KodeTransaksi: 'A001',
          namapembeli: 'cica syifa',
          namabarang: 'Mixer Miyako',
          hargabarang: 'Rp.165.000',
          jumlahbarang: '2',
          total: 'Rp.330.000'
        },
        {
          KodeTransaksi: 'A002',
          namapembeli: 'arafah',
          namabarang: 'Oven Kirin',
          hargabarang: 'Rp.550.000',
          jumlahbarang: '1',
          total: 'Rp.550.0000'
        },
        {
          KodeTransaksi: 'A003',
          namapembeli: 'bintang',
          namabarang: 'Magic com cosmo',
          hargabarang: 'Rp.233.000',
          jumlahbarang: '3',
          total: 'Rp.699.000'
        }
      ]
    }
  },

  methods: {
    // emulate fetching data from server
    addRow () {
      this.loading = true
      setTimeout(() => {
        const
          index = Math.floor(Math.random() * (this.data.length + 1)),
          row = this.original[Math.floor(Math.random() * this.original.length)]
        if (this.data.length === 0) {
          this.rowCount = 0
        }
        row.id = ++this.rowCount
        const addRow = { ...row } // extend({}, row, { name: `${row.name} (${row.__count})` })
        this.data = [...this.data.slice(0, index), addRow, ...this.data.slice(index)]
        this.loading = false
      }, 500)
    },

    removeRow () {
      this.loading = true
      setTimeout(() => {
        const index = Math.floor(Math.random() * this.data.length)
        this.data = [...this.data.slice(0, index), ...this.data.slice(index + 1)]
        this.loading = false
      }, 500)
    }
  }
}
</script>
