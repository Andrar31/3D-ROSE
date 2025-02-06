# 3D-ROSE
ROSE 3D'S FOR VALENTINE'S DAY
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>3D Rose</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
    <style>
        body { margin: 0; }
        canvas { display: block; }
    </style>
</head>
<body>
    <script>
        // Escena
        const scene = new THREE.Scene();
        const camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
        const renderer = new THREE.WebGLRenderer();
        renderer.setSize(window.innerWidth, window.innerHeight);
        document.body.appendChild(renderer.domElement);

        // Luz
        const light = new THREE.PointLight(0xffffff, 1.5);
        light.position.set(10, 10, 10);
        scene.add(light);

        // Geometría de la rosa
        const petals = new THREE.Group();
        for (let i = 0; i < 10; i++) {
            const geometry = new THREE.ConeGeometry(1, 2, 10);
            const material = new THREE.MeshPhongMaterial({ color: 0xff0000 });
            const petal = new THREE.Mesh(geometry, material);
            petal.position.y = i * 0.3;
            petal.rotation.y = i * 0.5;
            petals.add(petal);
        }
        scene.add(petals);

        // Posición de la cámara
        camera.position.z = 10;

        // Animación
        function animate() {
            requestAnimationFrame(animate);
            petals.rotation.y += 0.01;
            renderer.render(scene, camera);
        }
        animate();
    </script>
</body>
</html>
