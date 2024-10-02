<template>
    <div class="customization-container">
      <h2>Customize Your Mug</h2>
      <div class="customization-options">
        <label for="color">Color:</label>
        <button @click="toggleColorPalette" style="width:150px;height:40px; border-radius:3px;" class="neumorphic-button">Change Color</button>
        <div v-if="showColorPalette" class="color-palette">
          <div
            v-for="color in colors"
            :key="color"
            :style="{ backgroundColor: color }"
            class="color-swatch"
            @click="updateColor(color)"
          ></div>
        </div>
        <div class="selected-color" :style="{ backgroundColor: selectedColor }"></div>
  
        <label>Size:</label>
        <button @click="updateSize('S')">Small</button>
        <button @click="updateSize('M')">Medium</button>
        <button @click="updateSize('L')">Large</button>
  
       
  
        <label for="text">Text:</label>
        <input v-model="customText" id="text" placeholder="Enter your text" />
  
        <label for="font">Font:</label>
        <select v-model="selectedFont" id="font" @change="updateText">
          <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
        </select>
  
        <label>
          <input type="checkbox" v-model="isBold" @change="updateText" /> Bold
        </label>
        <label>
          <input type="checkbox" v-model="isItalic" @change="updateText" /> Italic
        </label>
  
        <input type="file" @change="onImageChange" />
      </div>
      <div ref="container" id="3d-container"></div>
    </div>
  </template>
  
  
  
  
  
 
 <script>
import { ref, onMounted, watch } from 'vue';
import * as THREE from 'three';
import { OrbitControls } from 'three/examples/jsm/controls/OrbitControls.js';

export default {
  setup() {
    const container = ref(null);
    const selectedColor = ref('white');
    const colors = [
      '#FF0000', '#FF3333', '#FF6666', '#FF9999', '#FFCCCC', // Red shades
      '#0000FF', '#3333FF', '#6666FF', '#9999FF', '#CCCCFF', // Blue shades
      '#00FF00', '#33FF33', '#66FF66', '#99FF99', '#CCFFCC', // Green shades
      '#FFFF00', '#FFFF33', '#FFFF66', '#FFFF99', '#FFFFCC', // Yellow shades
      '#FF00FF', '#FF33FF', '#FF66FF', '#FF99FF', '#FFCCFF', // Pink shades
      '#00FFFF', '#33FFFF', '#66FFFF', '#99FFFF', '#CCFFFF'  // Cyan shades
    ];
    const sizes = { S: 1, M: 1.2, L: 1.5 };
    const customText = ref('');
    const selectedFont = ref('Arial');
    const fonts = ['Arial', 'Courier New', 'Georgia', 'Times New Roman', 'Verdana'];
    const isBold = ref(false);
    const isItalic = ref(false);
    const showColorPalette = ref(false);
    const textPlacementMode = ref(false);
    let scene, camera, renderer, mug, textMesh, textureMesh, controls, raycaster, mouse;

    onMounted(() => {
      initThree();
    });

    const initThree = () => {
      scene = new THREE.Scene();
      camera = new THREE.PerspectiveCamera(75, window.innerWidth / window.innerHeight, 0.1, 1000);
      camera.position.z = 5;

      renderer = new THREE.WebGLRenderer({ antialias: true });
      renderer.setSize(window.innerWidth, window.innerHeight);
      renderer.shadowMap.enabled = true;
      container.value.appendChild(renderer.domElement);

      const outerBodyGeometry = new THREE.CylinderGeometry(1, 1, 2, 32);
      const outerBodyMaterial = new THREE.MeshPhongMaterial({ color: selectedColor.value, shininess: 150 });
      const outerBody = new THREE.Mesh(outerBodyGeometry, outerBodyMaterial);
      outerBody.castShadow = true;

      const innerBodyGeometry = new THREE.CylinderGeometry(0.95, 0.95, 1.9, 32);
      const innerBodyMaterial = new THREE.MeshPhongMaterial({ color: selectedColor.value, shininess: 150, side: THREE.DoubleSide });
      const innerBody = new THREE.Mesh(innerBodyGeometry, innerBodyMaterial);
      innerBody.position.y = -0.05;
      innerBody.castShadow = true;

      const bottomGeometry = new THREE.CircleGeometry(0.95, 32);
      const bottomMaterial = new THREE.MeshPhongMaterial({ color: selectedColor.value, shininess: 150 });
      const bottom = new THREE.Mesh(bottomGeometry, bottomMaterial);
      bottom.rotation.x = -Math.PI / 2;
      bottom.position.y = -1;

      const handleGeometry = new THREE.TorusGeometry(0.4, 0.1, 16, 100);
      const handleMaterial = new THREE.MeshPhongMaterial({ color: selectedColor.value, shininess: 150 });
      const handle = new THREE.Mesh(handleGeometry, handleMaterial);
      handle.position.set(1.2, 0, 0);
      handle.rotation.z = Math.PI / 2;
      handle.castShadow = true;

      mug = new THREE.Group();
      mug.add(outerBody);
      mug.add(innerBody);
      mug.add(bottom);
      mug.add(handle);
      scene.add(mug);

      controls = new OrbitControls(camera, renderer.domElement);
      controls.enableDamping = true;
      controls.dampingFactor = 0.25;
      controls.enableZoom = true;

      const ambientLight = new THREE.AmbientLight(0xffffff, 0.5);
      scene.add(ambientLight);

      const dirLight = new THREE.DirectionalLight(0xffffff, 1);
      dirLight.position.set(5, 5, 5);
      dirLight.castShadow = true;
      scene.add(dirLight);

      raycaster = new THREE.Raycaster();
      mouse = new THREE.Vector2();

      window.addEventListener('click', onMouseClick);

      animate();
    };

    const animate = () => {
      requestAnimationFrame(animate);
      controls.update();
      renderer.render(scene, camera);
    };

    const updateColor = (color) => {
      selectedColor.value = color;
      mug.children.forEach(part => {
        part.material.color.set(color);
      });
      showColorPalette.value = false;
    };

    const toggleColorPalette = () => {
      showColorPalette.value = !showColorPalette.value;
    };

    const updateSize = (size) => {
      mug.scale.set(sizes[size], sizes[size], sizes[size]);
    };

    const updateText = (position) => {
      if (textMesh) scene.remove(textMesh);

      const fontLoader = new THREE.FontLoader();
      fontLoader.load('path/to/font.json', (font) => {
        const textGeometry = new THREE.TextGeometry(customText.value, {
          font: font,
          size: 0.2,
          height: 0.05,
          bevelEnabled: true,
          bevelThickness: 0.01,
          bevelSize: 0.02,
          bevelOffset: 0,
          bevelSegments: 5
        });

        const textMaterial = new THREE.MeshPhongMaterial({ color: 0x000000 });
        textMesh = new THREE.Mesh(textGeometry, textMaterial);

        textMesh.position.copy(position);
        textMesh.lookAt(camera.position);
        scene.add(textMesh);
      });
    };

    const onImageChange = (event) => {
      const file = event.target.files[0];
      const reader = new FileReader();

      reader.onload = (e) => {
        const textureLoader = new THREE.TextureLoader();
        textureLoader.load(e.target.result, (texture) => {
          // Create a cylindrical geometry for the mug
          const mugGeometry = new THREE.CylinderGeometry(1, 1, 2, 64, 1, true);
          const mugMaterial = new THREE.MeshPhongMaterial({ color: selectedColor.value, shininess: 150 });
          const mug = new THREE.Mesh(mugGeometry, mugMaterial);

          // Create a geometry for the image texture
          const imageGeometry = new THREE.CylinderGeometry(1.01, 1.01, 2, 64, 1, true);
          const imageMaterial = new THREE.MeshBasicMaterial({
            map: texture,
            transparent: true,
            side: THREE.DoubleSide,
          });
          const imageMesh = new THREE.Mesh(imageGeometry, imageMaterial);

            // Adjust the UV mapping to place the image on the side opposite the handle
            const uv = imageGeometry.attributes.uv;
            for (let i = 0; i < uv.count; i++) {
                const u = uv.getX(i);
                const v = uv.getY(i);
                if (u >= 0.25 && u <= 0.75) {
                    uv.setX(i, (u - 0.25) * 2);  // Map U coordinates to the range [0, 1] for the front half
                } else {
                    uv.setX(i, 0);  // Remove the texture from the back half
                }
            }
            uv.needsUpdate = true;

            // Position the image mesh correctly on the mug
            imageMesh.rotation.y = Math.PI / 2; // Rotate the image to place it on the side
            mug.add(imageMesh);

            // Rotate the mug to ensure the handle is positioned correctly
            mug.rotation.y = Math.PI / 2; // Rotate the mug to move the handle to the side

            scene.add(mug);

            // Ensure the image mesh is correctly positioned
            imageMesh.position.set(0, 0, 0);  // Adjust as needed
        });
    };

    reader.readAsDataURL(file);
};





  
      const onMouseClick = (event) => {
  if (!textPlacementMode.value) return;

  mouse.x = (event.clientX / window.innerWidth) * 2 - 1;
  mouse.y = -(event.clientY / window.innerHeight) * 2 + 1;

  raycaster.setFromCamera(mouse, camera);

  const intersects = raycaster.intersectObjects(mug.children, true);
  if (intersects.length > 0) {
    const intersect = intersects[0];
    updateText(intersect.point);
    textPlacementMode.value = false;
  }
};


    const enableTextPlacement = () => {
      textPlacementMode.value = true;
    };

    watch(selectedColor, (newColor) => {
      updateColor(newColor);
    });
    watch(customText, (newText) => {
      if (textMesh) updateText(textMesh.position);
    });
    watch(selectedFont, updateText);
    watch(isBold, updateText);
    watch(isItalic, updateText);

    return {
      container,
      selectedColor,
      colors,
      sizes,
      customText,
      selectedFont,
      fonts,
      isBold,
      isItalic,
      updateSize,
      onImageChange,
      updateColor,
      toggleColorPalette,
      showColorPalette,
      enableTextPlacement,
      textPlacementMode,
    };
  }
};
</script>

  
  

<style scoped>
.customization-container {
  text-align: center;
  margin: 20px;
}

.customization-options {
  margin-bottom: 20px;
}

.neumorphic-button {
  background: #e0e0e0;
  border-radius: 10px;
  box-shadow: 5px 5px 10px #bebebe,
              -5px -5px 10px #ffffff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  transition: box-shadow 0.3s ease;
}

.neumorphic-button:active {
  box-shadow: inset 5px 5px 10px #bebebe,
              inset -5px -5px 10px #ffffff;
}

.color-palette {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 5px;
  margin-bottom: 20px;
}

.color-swatch {
  width: 30px;
  height: 30px;
  cursor: pointer;
  border: 2px solid #000;
}

.color-swatch:hover {
  border: 2px solid #fff;
}

#3d-container {
  width: 100%;
  height: 500px;
}
</style>
