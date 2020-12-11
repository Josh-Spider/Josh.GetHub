## Sea bienvenido
## Este proyecto fue posible gracias a a las redes neuronales
## Que son las redes neuroanles
Origen y desarrollo del concepto de Red Neuronal.. Las primeras investigaciones sobre el tema, datan apr o ximadamente
## Cuál es su relacion con la tería de grafoas
Sea V el conjunto no vacío de vértices o nodos y E el conjunto de lados o aristas (pares de vértices); se dice que G es un grafo, si G= (V, E) es una estructura de datos compuesta por esos dos conjuntos V y E que forman un conjunto de pares ordenados o desordenados de vértices o nodos. Los pares de vértices van entre paréntesis y los pares desordenados, pondrán entre llaves.
![Grafo](https://image.slidesharecdn.com/teoriadegrafos-120519092421-phpapp01/95/teoria-de-grafos-9-728.jpg%3Fcb%3D1416524540)

<img src="https://andromedavaluecapital.com/wp-content/uploads/2018/02/neuronal-network-1024x585.jpg" alt="Red neuronal">

![Grafo](https://www.madrimasd.org/blogs/matematicas/files/2012/09/Network_representation_of_brain_connectivity.jpg)


<img src="https://image.slidesharecdn.com/redesneuronales-090531152733-phpapp02/95/redes-neuronales-2-728.jpg?cb=1243784481">

![Grafo](https://www.madrimasd.org/blogs/matematicas/files/2012/09/Network_representation_of_brain_connectivity.jpg)
    // Load the image model and setup the webcam
    async function init() {
        const modelURL = URL + "model.json";
        const metadataURL = URL + "metadata.json";

        // load the model and metadata
        // Refer to tmImage.loadFromFiles() in the API to support files from a file picker
        // or files from your local hard drive
        // Note: the pose library adds "tmImage" object to your window (window.tmImage)
        model = await tmImage.load(modelURL, metadataURL);
        maxPredictions = model.getTotalClasses();

        // Convenience function to setup a webcam
        const flip = true; // whether to flip the webcam
        webcam = new tmImage.Webcam(200, 200, flip); // width, height, flip
        await webcam.setup(); // request access to the webcam
        await webcam.play();
        window.requestAnimationFrame(loop);

        // append elements to the DOM
        document.getElementById("webcam-container").appendChild(webcam.canvas);
        labelContainer = document.getElementById("label-container");
        for (let i = 0; i < maxPredictions; i++) { // and class labels
            labelContainer.appendChild(document.createElement("div"));
        }
    }

    async function loop() {
        webcam.update(); // update the webcam frame
        await predict();
        window.requestAnimationFrame(loop);
    }

    // run the webcam image through the image model
    async function predict() {
        // predict can take in an image, video or canvas html element
        const prediction = await model.predict(webcam.canvas);
        for (let i = 0; i < maxPredictions; i++) {
            const classPrediction =
                prediction[i].className + ": " + prediction[i].probability.toFixed(2);
            labelContainer.childNodes[i].innerHTML = classPrediction;
        }
    }
</script>


