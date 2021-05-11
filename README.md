<PHP1>

<!DOCTYPE html>
<html>
    <head>
        <title>Registrasi</title>
    </heaad>
    <body>
        <form action="Praktikum7_Web1.php" method="POST">
            <Fieldset>
                <h1>Form Input Data Pegawai</h1>
            <p>
                <label>Nama Pegawai :</label>
                <input type="text" name="nama">
            </p>
            <p>
                <label>Tanggal lahir :</label>
                <input  name="tanggal_lahir">
            </p>

            <p>
                <label>Jenis pegawai :</label>
                <select name="jenis_pegawai">
                    <option value="Kontrak">Kontrak</option>
                    <option value="Tetap">Tetap</option>
                </select>
            </p>
            <p>
                <label>Posisi :</label><br>
                <label><input type="radio" name="job" value="Operator">Operator</label>
                <label><input type="radio" name="job" value="Leader">Leader</label>
                <label><input type="radio" name="job" value="Supervisor">Supervisor</label>
            </p>
            <p>
                <label>Total jam kerja : </label>
                <input type="number" name="jam_kerja"/>
            </p>
            <p>
                <input type="submit" name="submit" value="Hitung"/>
            </p>
            </fieldset>
        </form>
</body>
</html>


<PHP2>

<?php
$nama = $_POST['nama'];
$tanggal_lahir = $_POST['tanggal_lahir'];
$jenis_pegawai = $_POST['jenis_pegawai'];
$job =  $_POST['job'];
$jam_kerja = $_POST['jam_kerja'];

function hitung_umur($tanggal_lahir) {
    $birthDate = new dateTime($tanggal_lahir);
    $today = new DateTime("today");
    if ($birthDate > $today){
        exit("0 tahun 0 bulan 0 hari");
    }
    $y = $today->diff($birthDate)->y;
    $m = $today->diff($birthDate)->m;
    $d = $today->diff($birthDate)->d;
    return $y." tahun ". $m." bulan ".$d." hari ";
}
echo "umur anda :";
echo hitung_umur("24-05-1997");


if($jenis_pegawai == 'Kontrak'){
    if($job== 'Operator'){
        $gaji_perjam = 270000;
    }elseif($job== 'Leader'){
        $gaji_perjam = 300000;
    }elseif($job== 'Supervisor'){
        $gaji_perjam = 320000;
}
}elseif($jenis_pegawai == 'Tetap'){
    if($job== 'Operator'){
        $gaji_perjam = 290000;
    }elseif($job== 'Leader'){
        $gaji_perjam = 300000;
    }elseif($job== 'Supervisor'){
        $gaji_perjam = 350000;
}
}

$gaji_pokok = $gaji_perjam * $jam_kerja;

?>

<table>
    <tr>
        <td>Nama Karyawan : <?php echo ucwords($nama); ?></td>
    </tr>
    <tr>
        <td>Tanggal lahir : <?php echo ucwords($tanggal_lahir); ?></td>
    </tr>
    <tr>
    
        <td>Jenis Pegawai : <?php echo ucwords($jenis_pegawai); ?></td>
    </tr>
    <tr>
        <td>Posisi : <?php echo ucwords($job); ?></td>
    </tr>
    <tr>
        <td>Tarif Perjam : <?php echo $gaji_perjam; ?></td>
    </tr>
    <tr>
        <td>Total Jam Kerja : <?php echo $jam_kerja. 'jam'; ?></td>
    </tr>
    <tr>
        <td>Upah : <?php echo $gaji_pokok; ?></td>
    </tr>

</table>
