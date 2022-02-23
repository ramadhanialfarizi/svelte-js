<script>
    import { Table } from 'sveltestrap';

    // data dummy, anggap ini seperti data json dari backend
    let user = [
        {
            id: '1',
            firstname: 'joko',
            lastname: 'endwar',
            username: 'joeko'
        },
        {
            id: '2',
            firstname: 'dono',
            lastname: 'kasino',
            username: 'doa'
        },
        {
            id: '3',
            firstname: 'jane',
            lastname: 'doe',
            username: 'janet'
        }
    ]

    // menggunakan const karena akan di deklarasikan pada html dibawah
    const Hapus = (id) => {
        // filter = fungsi untuk memfilter di javascript
        user = user.filter((us)=> us.id != id)
    }
  </script>
  
  <Table>
    <thead>
      <tr>
        <th>#</th>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Username</th>
        <th>Aksi</th>
      </tr>
    </thead>
    <tbody>
        <!-- looping each, menggunakan #each ... as ... menambahkan kunci yang bersifat unik untuk event handler atau melakukan aksi-->
        {#each user as us, id (us.id)}
        <tr>
            <th scope="row">{id + 1}</th>
            <td>{us.firstname}</td>
            <td>{us.lastname}</td>
            <td>{us.username}</td>
            <!-- ()=> berfungsi untuk mendeteksi parameter id -->
            <td><button on:click={()=>Hapus(us.id)}>Hapus</button></td>
        </tr>
        {:else}
            <p>Data not found</p>
        {/each}
    </tbody>
  </Table>