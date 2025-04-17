# LetterWebGL
Implement 2D Rotating, Translation, Scaling Matrix in WebGL

Implementasi 2D Rotating, Translation, Scaling Matrix dalam WebGL, saya berhasil mengimplemntasikan dengan letter 'L', dimana bentuk tersebut berwarna pink. 
 ```
function setL(gl){
    gl.bufferData(
        gl.ARRAY_BUFFER,
        new Float32Array([
             // Left part of L
             0, 0, 
             30, 0,
             0, 120,
             0, 120,
             30, 0,
             30, 120,
 
             // Bottom part of L
             0, 120,
             80, 120,
             80, 80,
             0, 120,
             80, 80,
             0, 80,
        ]),
        gl.STATIC_DRAW
    );
}
```
Dalam pembuatan kode ini, saya memerlukan 3 file, yaitu css, js dan html
- css : Kode CSS ini mendefinisikan gaya untuk elemen HTML dalam aplikasi WebGL, dengan fokus pada tampilan dan interaksi antarmuka pengguna. Ia mengatur tata letak responsif untuk berbagai ukuran layar dan mendukung mode gelap, meningkatkan keterbacaan dan aksesibilitas. Selain itu, pengaturan khusus untuk elemen canvas memastikan tampilan yang konsisten dan menarik, baik dalam tampilan biasa maupun dalam iframe.
- js : Kode ini menginisialisasi aplikasi WebGL untuk menggambar bentuk huruf "L" yang dapat diputar, diubah bentuk dan dipindahkan di canvas. Shader vertex dan fragment diproses dan dihubungkan ke program GLSL, sementara antarmuka pengguna memungkinkan pengguna untuk mengubah posisi rotasi melalui slider. Fungsi drawScene bertanggung jawab untuk memperbarui dan menggambar ulang objek di canvas setiap kali ada perubahan input.
    ```
    var rotationLocation = gl.getUniformLocation(program, "u_rotation");
    var translationLocation = gl.getUniformLocation(program, "u_translation");
    var scaleLocation = gl.getUniformLocation(program, "u_scale");

    ...

    var translation = [100, 0];
    var rotation = [0, 1];
    var scale = [1, 1];

    ...
    
    webglLessonsUI.setupSlider("#x", {value: rotation[0], slide: updatePosition(0), max: gl.canvas.width });
    webglLessonsUI.setupSlider("#y", {value: rotation[1], slide: updatePosition(1), max: gl.canvas.height});
    webglLessonsUI.setupSlider("#angle", {slide: updateAngle, max: 360});
    
    webglLessonsUI.setupSlider("#scaleX", {value: scale[0], slide: updateScale(0), min: 0, max: 10, step: 0.01, precision: 2});
    webglLessonsUI.setupSlider("#scaleY", {value: scale[1], slide: updateScale(1), min: 0, max: 10, step: 0.01, precision: 2});

    webglLessonsUI.setupSlider("#x", {value: translation[0], slide: updatePosition(0), max: gl.canvas.width });
    webglLessonsUI.setupSlider("#y", {value: translation[1], slide: updatePosition(1), max: gl.canvas.height});
    ```
- html : Kode ini mengatur elemen canvas dan antarmuka pengguna untuk aplikasi WebGL yang menampilkan objek yang dapat diputar, diubah, dan dipindahkan. Shader vertex mengelola rotasi, skala, dan translasi posisi titik sebelum menggambar, sementara shader fragment menetapkan warna objek. Dengan menggunakan dua skrip eksternal, webgl-lessons-ui.js dan rotating.js, aplikasi ini berinteraksi dengan antarmuka pengguna untuk mengubah parameter rotasi secara dinamis.

- Output Result Rotating
  <img width="1440" alt="Screenshot 2024-09-22 at 11 54 24" src="https://github.com/user-attachments/assets/17ad3a36-3ca6-49b8-94ff-1eee1761affc">
- Output Result Translating
  <img width="1440" alt="Screenshot 2024-09-22 at 11 54 41" src="https://github.com/user-attachments/assets/cba5a5bf-709d-4215-9dee-6223267fb078">
- Output Result Scaling
<img width="1440" alt="Screenshot 2024-09-22 at 11 54 33" src="https://github.com/user-attachments/assets/00dac464-a999-4f96-8f22-6dc22769eae4">
