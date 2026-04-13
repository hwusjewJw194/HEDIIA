# Curso Completo de Inteligencia Artificial (IA) - Guía del Curso

Bienvenida

Este documento describe la estructura completa del curso de Inteligencia Artificial que se encuentra en este repositorio. El objetivo es ofrecer un recorrido didáctico desde los conceptos básicos hasta técnicas avanzadas, con teoría, ejemplos de código, ejercicios y recursos descargables.

Objetivos del curso

- Entender los fundamentos matemáticos y conceptuales de la IA.
- Implementar algoritmos clásicos y modernos en Python.
- Diseñar, entrenar y evaluar modelos de machine learning y deep learning.
- Desplegar modelos y comprender aspectos de producción y ética.

Estructura general

1. Nivel Principiante (principiante/)
   - Fundamentos de Python y matemáticas para IA
   - Regresión, clasificación, clustering
   - Perceptrón y redes neuronales simples
   - Primeros proyectos con datasets sencillos

2. Nivel Intermedio (intermedio/)
   - Redes neuronales profundas (MLP, CNN, RNN)
   - Entrenamiento, optimización y regularización
   - Transfer learning y modelos preentrenados
   - Proyectos prácticos: visión por computador, NLP básico

3. Nivel Experto (experto/)
   - Transformers y modelos a gran escala
   - Aprendizaje por refuerzo, generación y evaluación avanzada
   - MLOps, despliegue en producción, optimización y cuantización
   - Ética, privacidad y gobernanza de modelos

4. Modelos y recursos descargables (modelos/)
   - Enlaces y guías para descargar modelos abiertos y usarlos localmente

5. Recursos adicionales (recursos/)
   - Libros, cursos, datasets, herramientas y comunidades recomendadas

Prerrequisitos

- Conocimientos básicos de programación (recomendado Python)
- Álgebra lineal, cálculo y probabilidad (nivel introductorio)
- Equipo con Python 3.8+ instalado; preferible GPU para deep learning

Instalación y entorno de trabajo

1. Crear un entorno virtual:

   python -m venv venv
   source venv/bin/activate  # Linux/macOS
   venv\Scripts\activate     # Windows

2. Instalar dependencias básicas (ejemplo):

   pip install --upgrade pip
   pip install numpy scipy pandas matplotlib scikit-learn jupyterlab
   pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu117  # o versión CPU
   pip install transformers datasets huggingface-hub
   pip install seaborn tqdm notebook

Recomendaciones de evaluación

- Cada nivel contiene ejercicios y mini-proyectos que deben completarse para consolidar conocimientos.
- Recomiendo usar notebooks Jupyter para experimentación y GitHub para control de versiones.

Contribuciones

- Si quieres contribuir: abre un issue o un pull request. Sigue las buenas prácticas: explica el cambio, añade tests o notebooks reproducibles y actualiza esta guía si añades material nuevo.

Contacto

Para dudas o colaboración: hwusjewJw194 (Hedy Sánchez)

Licencia

Este curso y los materiales están publicados para fines educativos personales. Si incluyes modelos de terceros, respeta sus licencias. Puedes añadir una licencia concreta aquí (por ejemplo MIT) si deseas permitir reutilización amplia.
