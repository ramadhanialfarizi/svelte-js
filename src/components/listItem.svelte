<script>
    import { ListGroup, ListGroupItem, Row, Col } from 'sveltestrap';

    // untuk bisa transfer data antar props, menggunakan export
    export let namaProduk = "kosong";
    export let Keterangan = "kosong";
</script>

<ListGroupItem>
    <Row>
        <Col>
            <img src="images/Samsung-Galaxy-A52-5G.jpg" alt="produk" width="100">
        </Col>
        <Col>
            <h5>{namaProduk}</h5>
            <p>{Keterangan}</p>
        </Col>
    </Row>

</ListGroupItem>