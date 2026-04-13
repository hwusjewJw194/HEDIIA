## Nivel Intermedio (intermedio/)

El nivel intermedio proporciona una comprensión profunda de las arquitecturas modernas de redes neuronales y las técnicas avanzadas para entrenar modelos efectivos. Este nivel permite trabajar con problemas complejos y datasets más grandes, preparando el camino hacia aplicaciones prácticas en visión por computadora y procesamiento de lenguaje natural.

### Redes neuronales profundas (MLP, CNN, RNN)

#### MLP (Multilayer Perceptron)

El perceptrón multicapa es la red neuronal densa fundamental que extiende los conceptos del nivel principiante.

- **Arquitectura mejorada**: Múltiples capas ocultas con centenares o miles de neuronas por capa.
- **Profundidad de red**: Capas adicionales permiten aprender representaciones jerárquicas complejas.
- **Conexiones densas**: Cada neurona en una capa conecta con todas las neuronas de la siguiente capa.
- **Capacidad de aprendizaje**: Capaz de aprender funciones no-lineales arbitrariamente complejas.
- **Aplicaciones**: Problemas de regresión y clasificación en datos tabulares, visión por computadora básica.
- **Desafíos**: Vanishing gradient problem en redes muy profundas, requiere normalización cuidadosa.

#### CNN (Convolutional Neural Networks - Redes Neuronales Convolucionales)

Las redes convolucionales están especializadas en procesar datos con estructura espacial, especialmente imágenes.

- **Capas convolucionales**: Aplican filtros que se deslizan sobre la entrada detectando características locales como bordes, texturas y patrones.
- **Filtros y kernels**: Matrices pequeñas (3x3, 5x5) que extraen características específicas de la imagen.
- **Pooling**: Reduce la dimensionalidad preservando características importantes mediante max-pooling o average-pooling.
- **Arquitecturas clásicas**: LeNet (primeras CNNs), AlexNet, VGG, ResNet, Inception.
- **Parámetros compartidos**: Los mismos pesos se reutilizan en diferentes posiciones, reduciendo parámetros totales.
- **Invariancia espacial**: Detecta características independientemente de su posición en la imagen.
- **Aplicaciones**: Clasificación de imágenes, detección de objetos, segmentación semántica, reconocimiento facial.
- **Ventajas**: Altamente eficiente para datos con correlación espacial, requiere menos datos que MLPs para visión.

#### RNN (Recurrent Neural Networks - Redes Neuronales Recurrentes)

Las redes recurrentes están diseñadas para procesar secuencias temporales y datos con dependencias a largo plazo.

- **Conexiones recurrentes**: Neuronas que reciben entrada de pasos de tiempo anteriores, manteniendo estado temporal.
- **Hidden state**: Vector que retiene información del pasado y se actualiza con cada nuevo elemento de la secuencia.
- **Despliegue en tiempo**: La misma red se aplica en múltiples pasos de tiempo.
- **LSTM (Long Short-Term Memory)**: Variante que resuelve el vanishing gradient problem mediante celdas de memoria con puertas (input, forget, output).
- **GRU (Gated Recurrent Unit)**: Versión simplificada de LSTM con menos parámetros pero desempeño similar.
- **Bidireccional RNN**: Procesa secuencias en ambas direcciones para capturar contexto completo.
- **Aplicaciones**: Procesamiento de lenguaje natural, predicción de series temporales, traducción automática, generación de texto, análisis de video.
- **Ventajas**: Maneja secuencias de longitud variable, captura dependencias temporales complejas.

### Entrenamiento, optimización y regularización

#### Estrategias de entrenamiento avanzado

El entrenamiento de redes profundas requiere técnicas sofisticadas para converger eficientemente.

- **Batch normalization**: Normaliza las activaciones de cada capa para estabilizar el entrenamiento y permitir tasas de aprendizaje mayores.
- **Early stopping**: Detiene el entrenamiento cuando el desempeño en validación deja de mejorar, evitando sobreajuste.
- **Learning rate scheduling**: Ajusta la tasa de aprendizaje durante el entrenamiento, comenzando alto y disminuyendo progresivamente.
- **Warm-up**: Incrementa gradualmente la tasa de aprendizaje al inicio del entrenamiento para evitar inestabilidad.
- **Gradient accumulation**: Acumula gradientes de múltiples batches antes de actualizar pesos, simulando batches más grandes.

#### Optimizadores

Los optimizadores ajustan los pesos de la red basándose en los gradientes calculados.

- **SGD (Stochastic Gradient Descent)**: Algoritmo básico que actualiza pesos basándose en muestras individuales o mini-batches.
- **Momentum**: Mantiene velocidad de actualización acumulando gradientes anteriores para convergencia más rápida.
- **Adam (Adaptive Moment Estimation)**: Combina momentum con normalización adaptativa de tasa de aprendizaje. Es el optimizador más popular actualmente.
- **RMSprop**: Normaliza la tasa de aprendizaje por parámetro basándose en histórico de gradientes.
- **AdaGrad**: Reduce la tasa de aprendizaje para parámetros que han recibido grandes actualizaciones.
- **Comparación**: Adam es generalmente más robusto, SGD+Momentum puede lograr mejor generalización en algunos casos.

#### Regularización para prevenir sobreajuste

La regularización previene que el modelo memorice datos de entrenamiento en lugar de aprender patrones generalizables.

- **L1 y L2 regularization**: Añaden penalizaciones al término de pérdida que castiguen pesos grandes. L1 promueve esparsidad, L2 penaliza pesos grandes.
- **Dropout**: Desactiva aleatoriamente neuronas durante el entrenamiento, forzando la red a aprender representaciones redundantes y robustas.
- **Data augmentation**: Amplía el conjunto de entrenamiento mediante transformaciones de datos (rotación, zoom, ruido en imágenes).
- **Early stopping**: Detiene el entrenamiento cuando el desempeño en validación comienza a empeorar.
- **Ensemble methods**: Entrena múltiples modelos y promedian predicciones para mejor generalización.

#### Funciones de pérdida especializadas

La función de pérdida guía el aprendizaje del modelo hacia objetivos específicos.

- **Cross-entropy**: Estándar para clasificación, mide divergencia entre distribuciones predichas y reales.
- **Mean Squared Error (MSE)**: Para regresión, promedia cuadrados de errores.
- **Focal loss**: Enfatiza ejemplos difíciles de clasificar, útil para datasets desbalanceados.
- **Triplet loss**: Para aprendizaje de distancias en reconocimiento facial y verificación de identidad.
- **Contrastive loss**: Aprende representaciones donde ejemplos similares están cerca y diferentes están lejos.

### Transfer learning y modelos preentrenados

#### Concepto fundamental del Transfer Learning

El transfer learning aprovecha conocimiento aprendido en una tarea para mejorar desempeño en otra tarea relacionada.

- **Reutilización de características**: Modelos entrenados en datasets grandes aprenden características generales aplicables a otros problemas.
- **Reducción de datos requeridos**: Permite entrenar con datasets pequeños al aprovechar aprendizaje previo.
- **Ahorro computacional**: No requiere entrenar desde cero, significativamente más rápido.
- **Mejora de desempeño**: Modelos preentrenados frecuentemente superan modelos entrenados desde cero con datos limitados.

#### Tipos de Transfer Learning

- **Feature extraction**: Congela pesos de la red preentrenada y solo entrena capas finales. Útil cuando datos objetivo son limitados.
- **Fine-tuning**: Descongelan parcialmente o completamente pesos preentrenados y continúan entrenamiento con tasa de aprendizaje baja. Mejor cuando hay suficientes datos objetivo.
- **Domain adaptation**: Adapta modelos entre dominios relacionados pero diferentes.
- **Multi-task learning**: Entrena simultáneamente en múltiples tareas relacionadas compartiendo representaciones.

#### Modelos preentrenados populares

**Para visión por computadora**:
- **ImageNet models**: ResNet, VGG, Inception, MobileNet, EfficientNet entrenadas en millones de imágenes naturales.
- **YOLO**: Especializado en detección de objetos en tiempo real.
- **Mask R-CNN**: Para segmentación de instancias avanzada.
- **Vision Transformers (ViT)**: Arquitecturas basadas en transformers para visión.

**Para procesamiento de lenguaje natural**:
- **BERT**: Modelo bidireccional de Google, excelente para comprensión de texto.
- **GPT**: Modelo autoregresivo de OpenAI para generación de texto.
- **T5**: Modelo secuencia-a-secuencia para múltiples tareas NLP.
- **RoBERTa**: Versión mejorada de BERT con entrenamiento superior.
- **ELECTRA**: Modelo eficiente con mejor ratio precisión-tamaño.

#### Fuentes de modelos preentrenados

- **Hugging Face**: Repositorio principal con miles de modelos para NLP y visión, fácil integración.
- **TensorFlow Hub**: Colección de modelos preentrenados de Google.
- **PyTorch Hub**: Modelos oficiales y comunitarios para PyTorch.
- **Model Zoo**: Colecciones específicas de arquitecturas populares.

### Proyectos prácticos: Visión por computadora y NLP básico

#### Proyectos de Visión por Computadora

**Clasificación de imágenes avanzada**:
- Clasificación de objetos en fotos naturales usando CNN y transfer learning.
- Datasets: CIFAR-10/100, Caltech, PlantVillage para clasificación de enfermedades en plantas.
- Técnicas: Data augmentation, fine-tuning de ImageNet, ensemble de modelos.
- Evaluación: Matriz de confusión, curvas ROC, análisis de errores.

**Detección de objetos**:
- Localizar y clasificar múltiples objetos en una imagen con bounding boxes.
- Datasets: COCO (330K imágenes, 80 categorías), Pascal VOC, Open Images.
- Arquitecturas: Faster R-CNN, YOLO, SSD, RetinaNet.
- Métricas: mAP (mean Average Precision) en diferentes umbrales IoU.

**Segmentación semántica**:
- Clasificación pixel-por-pixel asignando clase a cada píxel de la imagen.
- Datasets: Cityscapes, Pascal VOC, ADE20K.
- Arquitecturas: FCN (Fully Convolutional Networks), U-Net, DeepLab, SegNet.
- Aplicaciones: Conducción autónoma, análisis médico, edición de fotos.

**Reconocimiento facial**:
- Detectar rostros, extraer características y reconocer identidades.
- Datasets: LFW (Labeled Faces in the Wild), VGGFace, CASIA-WebFace.
- Técnicas: FaceNet, ArcFace, Triplet loss para aprendizaje de distancias.
- Aplicaciones: Seguridad biométrica, verificación de identidad, conteo de presencia.

**Estimación de pose**:
- Detectar y rastrear puntos clave del cuerpo humano en imágenes y video.
- Datasets: COCO Keypoints, MPII, Human3.6M.
- Modelos: OpenPose, PoseNet, HRNet.
- Aplicaciones: Análisis de movimiento, deportes, realidad aumentada.

#### Proyectos de NLP Básico

**Análisis de sentimientos**:
- Clasificar textos como positivos, negativos o neutrales.
- Datasets: IMDb (películas), Twitter, producto reviews, SemEval.
- Técnicas: Embedding de palabras (Word2Vec, GloVe), RNN/LSTM, BERT fine-tuning.
- Aplicaciones: Monitoreo de marca, análisis de opinión de clientes, redes sociales.

**Clasificación de textos**:
- Categorizar documentos en temas predefinidos.
- Datasets: 20 Newsgroups, AG News, DBpedia, Yahoo Answers.
- Modelos: Bag-of-Words, TF-IDF, CNN de texto, RNN bidireccional.
- Aplicaciones: Spam detection, categorización de noticias, routing automático.

**Extracción de entidades nombradas (NER)**:
- Identificar y clasificar personas, lugares, organizaciones, fechas en texto.
- Datasets: CoNLL 2003, OntoNotes, SQuAD para contexto.
- Técnicas: BiLSTM-CRF (Conditional Random Fields), BERT + CRF.
- Aplicaciones: Extracción de información, procesamiento de documentos legales, búsqueda.

**Similitud de textos y búsqueda semántica**:
- Encontrar documentos similares o responder preguntas basándose en relevancia semántica.
- Datasets: STS (Semantic Textual Similarity), TREC, MS MARCO.
- Técnicas: Siamese networks, sentence transformers, embedding semánticos.
- Aplicaciones: Búsqueda de información, recomendaciones, detección de duplicados.

**Generación de resúmenes**:
- Crear versiones condensadas de textos largos preservando información clave.
- Datasets: CNN/DailyMail, XSum, SAMSum.
- Técnicas: Seq2Seq con attention, encoder-decoder, BERT abstractivo.
- Tipos: Resúmenes extractivos (seleccionar frases) o abstractivos (generar nuevas).

#### Estructura típica de un proyecto intermedio

1. **Selección del dataset**: Elegir dataset apropiado para la tarea, considerar tamaño, balance de clases, complejidad.
2. **Exploración y análisis**: Entender distribuciones, patrones, anomalías, desequilibrios.
3. **Preprocesamiento**: Limpieza, normalización, data augmentation específica de la tarea.
4. **Selección de arquitectura**: Elegir modelo base o arquitectura apropiada.
5. **Búsqueda de modelo preentrenado**: Considerar transfer learning para acelerar y mejorar.
6. **Configuración de entrenamiento**: Seleccionar optimizador, tasa de aprendizaje, schedule, regularización.
7. **Entrenamiento**: Monitorear métricas de entrenamiento y validación.
8. **Evaluación exhaustiva**: Usar múltiples métricas, análisis de errores, validación cruzada.
9. **Ajuste de hiperparámetros**: Optimizar performance mediante grid search o random search.
10. **Documentación y presentación**: Reportar resultados, mostrar ejemplos, analizar limitaciones.

#### Herramientas y librerías especializadas

- **PyTorch**: Framework flexible para redes profundas con API intuitiva.
- **TensorFlow/Keras**: Framework de Google con abstracciones de alto nivel.
- **Hugging Face Transformers**: Librería simplificada para usar modelos preentrenados NLP.
- **OpenCV**: Procesamiento de imágenes y visión por computadora.
- **NLTK y spaCy**: Librerías para procesamiento de lenguaje natural.
- **Scikit-image**: Procesamiento y análisis de imágenes.
- **Torchvision y TorchText**: Utilidades para visión y NLP en PyTorch.
- **Weights & Biases**: Plataforma para tracking de experimentos y visualización.
- **Jupyter/Colab**: Entornos interactivos con GPU disponible (Google Colab gratuito).
