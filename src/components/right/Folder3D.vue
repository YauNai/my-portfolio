<template>
  <section ref="folder-3d" @mousemove="mouseMove" id="folder-3d" class="grid-section">
    <div ref="threeContainer" id="bg" data-aos="fade"></div>

    <div data-aos="fade-up" style="text-align: center;">
      <button @click="doToPortfolio" class="my-btn portfolio-btn">所有作品</button>
    </div>

    <div class="content">
      <Works3D v-if="currPage === 'Works3D'" @doShowPage="doShowPage"/>

      <About3DWork v-if="currPage === 'AboutMagicBook'" subtitle="皮革製造流程動畫" title="魔法書" @doShowPage="doShowPage"/>
    </div>

    <div></div>
  </section>
</template>

<script setup>
  import { ref, onMounted, onBeforeUnmount, useTemplateRef } from 'vue';
  import * as THREE from 'three';
  import Works3D from './Works3D.vue';
  import About3DWork from './works/3d/About3DWork.vue';

  const currPage = ref('Works3D')
  const emit = defineEmits(['doShowPortfolio']);
  const threeContainer = ref(null);

  // Three.js 相關變數
  let scene, camera, renderer, animationId;
  let cube, gridLines = [], axisLines = [];
  const clock = new THREE.Clock()
  const sizes = {
    width: window.innerWidth,
    height: window.innerHeight
  }
  const cursor = { x: 5, y: 0 }

  const mouseMove = (e) => {
    cursor.x = e.clientX / sizes.width - 1.5
    cursor.y = e.clientY / sizes.height - 0.5
  }

  // 初始化 Three.js 場景
  const initThreeScene = () => {

    // 判斷初始畫面寬度
    if (window.innerWidth > 950) {
      sizes.width = window.innerWidth / 2
    }

    // 場景
    scene = new THREE.Scene();
    scene.background = new THREE.Color(0x3f3f3f);
    scene.fog = new THREE.Fog(0x3f3f3f, 15, 20);

    // 攝影機
    camera = new THREE.PerspectiveCamera(
      50,
      sizes.width / sizes.height,
      0.1,
      20
    );
    camera.position.x = -5;
    camera.position.y = 2;
    camera.position.z = 0;
    camera.lookAt(0, 0, 0);

    // 渲染器
    renderer = new THREE.WebGLRenderer({ antialias: true });
    renderer.setSize(sizes.width, sizes.height);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));

    // 將 canvas 加入到 Vue 管理的 DOM 中
    threeContainer.value.appendChild(renderer.domElement);

    // 建立場景物件
    createSceneObjects();

    // 開始動畫循環
    animate();
  };

  // 建立場景中的所有物件
  const createSceneObjects = () => {
    // 預設立方體
    const mBasic = new THREE.MeshPhongMaterial({ color: 0xe7e7e7 });
    const gCube = new THREE.BoxGeometry(1, 1, 1);
    cube = new THREE.Mesh(gCube, mBasic);
    scene.add(cube);

    // 平面網格線材質
    const mGridLine = new THREE.LineBasicMaterial({
      color: 0x545454,
      transparent: true,
      opacity: 0.8,
    });

    // X 軸方向的網格線
    const pointsGridX = [
      new THREE.Vector2(100, 0),
      new THREE.Vector2(-100, 0),
    ];
    const gGridX = new THREE.BufferGeometry().setFromPoints(pointsGridX);

    // Y 軸方向的網格線
    const pointsGridY = [
      new THREE.Vector3(0, 0, 100),
      new THREE.Vector3(0, 0, -100),
    ];
    const gGridY = new THREE.BufferGeometry().setFromPoints(pointsGridY);

    // 生成網格
    for (let i = -50; i < 50; i++) {
      const gridX = new THREE.Line(gGridX, mGridLine);
      gridX.position.z = i / 2;
      gridLines.push(gridX);
      scene.add(gridX);

      const gridY = new THREE.Line(gGridY, mGridLine);
      gridY.position.x = i / 2;
      gridLines.push(gridY);
      scene.add(gridY);
    }

    // X 軸
    const mAxisX = new THREE.LineBasicMaterial({ color: 0xff3352 });
    const pointsAxisX = [
      new THREE.Vector2(100, 0.001),
      new THREE.Vector2(-100, 0.001),
    ];
    const gAxisX = new THREE.BufferGeometry().setFromPoints(pointsAxisX);
    const axisX = new THREE.Line(gAxisX, mAxisX);
    axisLines.push(axisX);
    scene.add(axisX);

    // Y 軸
    const mAxisY = new THREE.LineBasicMaterial({ color: 0x8bdc00 });
    const pointsAxisY = [
      new THREE.Vector3(0, 0.001, 100),
      new THREE.Vector3(0, 0.001, -100),
    ];
    const gAxisY = new THREE.BufferGeometry().setFromPoints(pointsAxisY);
    const axisY = new THREE.Line(gAxisY, mAxisY);
    axisLines.push(axisY);
    scene.add(axisY);

    // 燈光
    const lightAmbient = new THREE.AmbientLight(0x404040, 10);
    const lightDirect = new THREE.DirectionalLight(0x404040, 10);
    lightDirect.position.set(-0.5, 0.4, 0.3);
    lightDirect.target.position.set(0, 0, 0);

    scene.add(lightAmbient, lightDirect);
  };

  // 動畫循環
  const animate = () => {
    const deltaTime = clock.getDelta()
    animationId = requestAnimationFrame(animate);

    // lerping
    const lerp = 1 - Math.pow(0.001, deltaTime * 3)

    camera.position.x += (Math.sin(cursor.x * Math.PI) * 5 - camera.position.x) * lerp
    camera.position.z += (Math.cos(cursor.x * Math.PI) * -5 - camera.position.z) * lerp
    camera.position.y += (cursor.y * -5 + 2 - camera.position.y) * lerp

    camera.lookAt(cube.position)
    renderer.render(scene, camera);
  };

  // 視窗大小調整
  const onWindowResize = () => {
    if (window.innerWidth > 950) {
      sizes.width = window.innerWidth / 2
    } else {
      sizes.width = window.innerWidth
    }

    sizes.height = window.innerHeight
    camera.aspect = sizes.width / sizes.height;
    renderer.setSize(sizes.width, sizes.height);

    camera.updateProjectionMatrix();
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  };

  // 切換到作品集頁面
  const section = useTemplateRef('folder-3d')
  const doToPortfolio = () => {
    threeContainer.value?.classList.add("fade-out");
    section.value.classList.add("slid-down");

    setTimeout(() => {
      emit('doShowPortfolio');
    }, 750);
  };

  // 切換到作品頁面
  const doShowPage = (page) => {
    currPage.value = page
  }


  // 元件掛載時初始化
  onMounted(() => {
    initThreeScene();
    window.addEventListener('resize', onWindowResize);
  });

  // 元件卸載時清理資源
  onBeforeUnmount(() => {
    // 移除事件監聽
    window.removeEventListener('resize', onWindowResize);

    // 停止動畫循環
    if (animationId) {
      cancelAnimationFrame(animationId);
    }

    // 清理 Three.js 資源
    if (scene) {
      scene.traverse((object) => {
        if (object.geometry) {
          object.geometry.dispose();
        }
        if (object.material) {
          if (Array.isArray(object.material)) {
            object.material.forEach(material => material.dispose());
          } else {
            object.material.dispose();
          }
        }
      });
    }

    // 清理渲染器
    if (renderer) {
      renderer.dispose();
      if (threeContainer.value && renderer.domElement) {
        threeContainer.value.removeChild(renderer.domElement);
      }
    }

    // 清空陣列
    gridLines = [];
    axisLines = [];
  });
</script>

<style scoped>
  .content {
    position: relative;
    z-index: 1;
  }

  #bg {
    position: fixed;
    width: 100%;
    height: 50%;
    left: 0;
    top: 0;
    z-index: -1;
    pointer-events: none;
  }

  #bg.fade-out {
    animation: fadeOut 0.75s forwards;
  }

  @keyframes fadeOut {
    to {
      opacity: 0;
    }
  }

  /* 確保 Three.js canvas 不會干擾互動 */
  #bg :deep(canvas) {
    display: block;
  }
</style>