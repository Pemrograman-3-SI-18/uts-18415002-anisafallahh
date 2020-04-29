<template>
  <q-page >
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
          <q-btn color="teal" :disable="loading" label="Tambah Data Barang" to="/admin/inputdataperabotan"/>
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
          label: 'Kode Barang',
          align: 'left',
          field: row => row.KodeBarang,
          format: val => `${val}`,
          sortable: true
        },
        { name: 'namabarang', align: 'center', label: 'Nama Barang', field: 'namabarang', sortable: true },
        { name: 'hargabarang', align: 'center', label: 'Harga Barang', field: 'hargabarang', sortable: true },
        { name: 'jumlahbarang', label: 'Jumlah Barang', align: 'center', field: 'jumlahbarang' },
        { name: 'Tanggalmasukbarang', label: 'Tanggal Masuk Barang', align: 'center', field: 'tanggalmasukbarang' }

      ],
      data: [
        {
          KodeBarang: 'A001',
          namabarang: 'Mixer Miyako',
          hargabarang: 'Rp.165.000',
          jumlahbarang: '48',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A002',
          namabarang: 'Oven Kirin',
          hargabarang: 'Rp.550.000',
          jumlahbarang: '45',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A003',
          namabarang: 'Teflon Maxim 26cm',
          hargabarang: 'Rp.127.000',
          jumlahbarang: '51',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A004',
          namabarang: 'Blender',
          hargabarang: 'Rp.233.000',
          jumlahbarang: '37',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A005',
          namabarang: 'Magic com Cosmo',
          hargabarang: 'Rp.253.000',
          jumlahbarang: '32',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A006',
          namabarang: 'Timbangan Digital',
          hargabarang: 'Rp.350.000',
          jumlahbarang: '34',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A007',
          namabarang: 'Dispenser Miyako',
          hargabarang: 'Rp.850.000',
          jumlahbarang: '23',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A008',
          namabarang: 'Container Box',
          hargabarang: 'Rp.216.000',
          jumlahbarang: '50',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A009',
          namabarang: 'Vacum Cleaner',
          hargabarang: 'Rp.2.500.000',
          jumlahbarang: '50',
          tanggalmasukbarang: '22-2-2020'
        },
        {
          KodeBarang: 'A0010',
          namabarang: 'Philips Setrika',
          hargabarang: 'Rp.150.000',
          jumlahbarang: '50',
          tanggalmasukbarang: '22-2-2020'
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
