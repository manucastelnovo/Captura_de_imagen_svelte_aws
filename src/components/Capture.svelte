    <h2>Hello OpenCV.js</h2>
    <div>
      <div class="inputoutput">
        <img id="imageSrc" alt="No Image" />
        
        <div class="caption">imageSrc 
            <input type="file" id="fileInput" name="file" />
        </div>
      </div>
    </div>

    <script type="text/javascript">

    let imgElement = document.getElementById("imageSrc");
    let inputElement = document.getElementById("fileInput");
    
    console.log(imgElement);
    console.log(inputElement);
    inputElement?.addEventListener("change", (e) => {
        imgElement.src = URL.createObjectURL(e.target.files[0]);
        console.log('hola')
    }, false);
    
    </script>
    