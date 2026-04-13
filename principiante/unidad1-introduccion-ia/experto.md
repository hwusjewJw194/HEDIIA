## Nivel Experto (experto/)

El nivel experto representa la frontera del conocimiento en Inteligencia Artificial moderna. Cubre arquitecturas de última generación, técnicas avanzadas de aprendizaje, producción industrial y consideraciones éticas críticas. Este nivel prepara profesionales para liderar proyectos innovadores y resolver problemas complejos del mundo real a escala empresarial.

### Transformers y modelos a gran escala

#### Arquitectura Transformer

Los transformers revolucionaron el procesamiento de secuencias al reemplazar RNNs con mecanismos de atención puros, permitiendo paralelización masiva y mejor captura de dependencias a largo plazo.

- **Mecanismo de atención**: Cada elemento de la secuencia puede atender directamente a todos los demás, calculando relevancia mediante consultas, claves y valores (Query-Key-Value).
- **Atención multi-cabeza (Multi-head attention)**: Múltiples representaciones de atención en paralelo, permitiendo atender a diferentes aspectos y posiciones simultáneamente.
- **Positional encoding**: Inyecta información de posición en la secuencia, esencial porque los transformers no tienen inherentemente sentido de orden temporal.
- **Capas feed-forward**: Redes densas aplicadas posición-por-posición después de atención, añadiendo capacidad no-lineal.
- **Normalización y residuales**: Layer normalization y conexiones residuales estabilizan el entrenamiento de redes muy profundas.
- **Ventajas sobre RNNs**: Paralelización completa permite entrenamiento en datasets masivos, mejor captura de dependencias a largo plazo, eficiencia computacional superior.

#### Modelos Transformer principales

**Modelos base**:
- **BERT (Bidirectional Encoder Representations from Transformers)**: Encoder transformer bidireccional preentrenado con masked language modeling. Excelente para tareas de comprensión de texto como clasificación y NER.
- **GPT (Generative Pretrained Transformer)**: Modelo autoregresivo que predice tokens secuencialmente. Base para GPT-2, GPT-3, GPT-4, especializados en generación de texto coherente.
- **T5 (Text-to-Text Transfer Transformer)**: Enmarca todas las tareas NLP como problemas texto-a-texto con encoder-decoder transformer. Versátil para múltiples tareas.
- **RoBERTa**: Versión mejorada de BERT con entrenamiento más largo y optimizaciones, típicamente mejor desempeño.

**Modelos de visión**:
- **Vision Transformer (ViT)**: Aplica arquitectura transformer a imágenes dividiéndolas en parches. Desempeño comparable o superior a CNNs con mejor escalabilidad.
- **CLIP (Contrastive Language-Image Pre-training)**: Entrena modelos a entender relación entre imágenes y texto, habilitando búsqueda cross-modal.
- **DeiT (Data-efficient image Transformers)**: ViT optimizado con técnicas de destilación para requerir menos datos.

**Modelos multimodales**:
- **DALL-E**: Genera imágenes a partir de descripciones textuales usando transformer decoder.
- **Flamingo**: Modelo de visión-lenguaje que puede hacer few-shot learning visual en tareas nuevas.
- **GPT-4V**: Extensión de GPT-4 que acepta imágenes como entrada además de texto.

**Modelos especializados**:
- **LLaMA (Large Language Model Meta AI)**: Modelos de lenguaje de código abierto eficientes en diferentes tamaños.
- **Mistral**: Modelo open-source competitivo con buena balance entre tamaño y capacidad.
- **CodeBERT y CodeT5**: Transformers especializado en entendimiento y generación de código.

#### Entrenamiento a gran escala

El entrenamiento de transformers masivos requiere infraestructura y técnicas especiales.

- **Distributed training**: Paralelización de datos entre múltiples GPUs/TPUs. Data parallelism (mismo modelo en múltiples dispositivos) y model parallelism (modelo dividido entre dispositivos).
- **Gradient checkpointing**: Ahorra memoria durante backpropagation eliminando cálculos intermedios y recalculándolos cuando se necesitan.
- **Mixed precision training**: Entrena usando precisión float16 mientras mantiene precisión float32 para cálculos sensibles, 2x más rápido con menos memoria.
- **Flash Attention**: Algoritmo de atención optimizado que reduce dramáticamente memoria y computación de attention, permitiendo secuencias más largas.
- **Contexto extendido**: Técnicas como RoPE (Rotary Position Embeddings) y ALiBi (Attention with Linear Biases) permiten extender longitud de contexto más allá del entrenamiento.
- **Datasets masivos**: GPT-3 entrenado en ~300 billones tokens, LLaMA en ~1.4 trillones tokens. Calidad de datos cada vez más importante.

#### Emergencia de capacidades y escalado

- **Leyes de escalado**: Relación matemática entre tamaño del modelo, datos de entrenamiento y desempeño. Modelos más grandes generalmente mejor desempeño.
- **Few-shot learning**: Modelos grandes pueden resolver nuevas tareas con solo pocos ejemplos, sin fine-tuning.
- **Prompting**: Técnicas para guiar modelos hacia respuestas deseadas. Zero-shot, few-shot, chain-of-thought prompting.
- **Emergent abilities**: Capacidades que aparecen en modelos grandes pero no en pequeños, como aritmética o reasoning complejo.

### Aprendizaje por refuerzo, generación y evaluación avanzada

#### Aprendizaje por Refuerzo (Reinforcement Learning)

El aprendizaje por refuerzo entrena agentes a tomar decisiones óptimas interactuando con un entorno y recibiendo recompensas.

- **Componentes clave**: Agente (entidad que aprende), entorno (mundo con el que interactúa), estado (situación actual), acciones (lo que el agente puede hacer), recompensas (señal de feedback), políticas (estrategia del agente).
- **Markov Decision Process (MDP)**: Formalismo matemático donde decisiones futuras dependen solo del estado actual, no del historial.
- **Value-based methods**: Aprenden función de valor que estima recompensa futura. Q-learning, Deep Q-Networks (DQN).
- **Policy-based methods**: Directamente aprenden política (mapa de estado a acción). Policy Gradient, Actor-Critic.
- **Model-based RL**: Aprende modelo del entorno para planificar futuras acciones.

#### Algoritmos clave de RL

- **Q-Learning**: Algoritmo fundamental que aprende función Q mediante bootstrapping. Offline, garantías de convergencia.
- **Deep Q-Networks (DQN)**: Combina Q-learning con redes profundas. Experience replay y target networks estabilizan entrenamiento.
- **Policy Gradient (PG)**: Optimiza directamente política usando gradientes. REINFORCE es algoritmo básico.
- **Actor-Critic**: Combina aprendizaje de valor (critic) con aprendizaje de política (actor). A3C, PPO, TRPO.
- **Proximal Policy Optimization (PPO)**: Algoritmo state-of-the-art, simple pero efectivo, usado en sistemas como ChatGPT.
- **Trust Region Policy Optimization (TRPO)**: Asegura actualizaciones de política conservativas.

#### Aplicaciones avanzadas de RL

- **Game playing**: AlphaGo derrotó campeones de Go usando tree search + redes neuronales profundas. AlphaZero juega ajedrez, shogi, go sin conocimiento previo.
- **Robótica**: Entrenamiento de robots para tareas complejas de manipulación. Sim-to-real transfer: entrenar en simulación y transferir a robots físicos.
- **Conducción autónoma**: Toma de decisiones en tiempo real en entornos complejos.
- **Optimización de infraestructuras**: Data centers, redes de telecomunicaciones, gestión de energía.
- **Recomendación personalizada**: Sistemas que balancean exploración (nuevas recomendaciones) y explotación (preferencias conocidas).

#### Alineación de modelos (Alignment)

Técnicas para alinear comportamiento de modelos con intenciones humanas, crítico para LLMs.

- **Reinforcement Learning from Human Feedback (RLHF)**: Entrena modelo de recompensa basado en preferencias humanas, luego optimiza política del modelo para maximizar esta recompensa. Usado para ChatGPT, Claude.
- **Direct Preference Optimization (DPO)**: Alternativa más eficiente a RLHF que no requiere entrenar modelo de recompensa separado.
- **Constitutional AI (CAI)**: Entrena modelos a seguir principios explícitos mediante critiques automáticas.
- **Mechanistic Interpretability**: Entiende cómo y por qué los modelos toman decisiones específicas.

#### Técnicas avanzadas de generación

Métodos para generar contenido de alta calidad de forma controlada.

- **Beam search**: Explora múltiples hipótesis en paralelo, mejor que greedy decoding pero más costoso.
- **Temperature sampling**: Controla aleatoriedad de generación. Temperatura baja = determinístico, alta = más creativo/errático.
- **Top-k y nucleus (Top-p) sampling**: Muestrea solo de tokens más probables, evita muestreo de colas improbables.
- **Constrained decoding**: Fuerza generación a respetar constraints (formato, tokens prohibidos).
- **Few-shot in-context learning**: Proporciona ejemplos en el prompt para guiar el estilo y formato de salida.
- **Controlled generation**: Dirige generación hacia atributos deseados (longitud, tone, contenido).

#### Evaluación avanzada de modelos

Evaluar modelos a gran escala requiere métricas sofisticadas más allá de accuracy simple.

- **BLEU y ROUGE**: Métricas de superposición n-gram para traducción automática y resúmenes. Conocen limitaciones (penalizan paráfrasis correctas).
- **METEOR**: Métrica más sofisticada que considera sinónimos y stemming.
- **BERTScore**: Compara embeddings BERT en lugar de tokens, mejor captura similitud semántica.
- **Evaluación por LLM**: Usa modelos de lenguaje como jueces para evaluar calidad de generación. Correlaciona bien con preferencias humanas.
- **Human evaluation**: Benchmark definitivo pero costoso. Acuerdos entre anotadores (inter-annotator agreement) miden consistencia.
- **Benchmarks estandarizados**: GLUE (lenguaje general), SuperGLUE (tareas difíciles), MMLU (conocimiento amplio), HellaSwag (razonamiento de sentido común).
- **Análisis de errores**: Categorizar y entender fallos del modelo, más informativo que métricas agregadas.
- **Robustez y generalization**: Evaluar desempeño en distribuciones diferentes, perturbaciones adversariales, casos edge.

### MLOps, despliegue en producción, optimización y cuantización

#### MLOps (Machine Learning Operations)

MLOps es la disciplina de operacionalizar ML, aplicando prácticas DevOps a ciclos de vida de modelos ML.

- **Versionado de datos y modelos**: DVC (Data Version Control), Weights & Biases, MLflow para rastrear experimentos, datos, modelos e hiperparámetros.
- **Reproducibilidad**: Documentar y reproducir exactamente experimentos. Seeds aleatorias, dependencias, configuraciones.
- **Automatización de pipelines**: Workflows automáticos que ejecutan preprocesamiento, entrenamiento, evaluación. Apache Airflow, Kubeflow, Jenkins.
- **CI/CD para ML**: Integración continua testea cambios de código, continuos despliegue entrena y despliega modelos automáticamente.
- **Feature stores**: Repositorios centralizados de features precalculadas y actualizadas. Tecton, Feast, para reutilizar features consistentemente.
- **Monitoreo y logging**: Rastrea desempeño, datos, computación durante entrenamiento e inferencia. Detecta degradación.

#### Despliegue en producción

Llevar modelos de ML de experimentos a sistemas productivos requiere consideraciones especiales.

- **Formatos de modelo**: ONNX (Open Neural Network Exchange) para portabilidad entre frameworks. SavedModel (TensorFlow), Pickle (PyTorch).
- **Contenedorización**: Docker empaqueta modelos con dependencias para deployment consistente. Kubernetes orquesta contenedores a escala.
- **APIs REST**: Expone modelos como servicios web HTTP. Flask, FastAPI para Python, permite múltiples clientes.
- **Batch vs. online serving**: Batch procesa datos en lotes offline (análisis histórico). Online sirve predicciones en tiempo real para usuarios.
- **Latencia y throughput**: Optimiza tiempo de predicción individual y número de predicciones por segundo.
- **Escalabilidad**: Maneja aumento de carga. Auto-scaling en cloud, load balancing distribuye requests.
- **Fallback strategies**: Comportamiento cuando modelo falla o degradación inaceptable. Versiones anteriores, heurísticas simples.
- **A/B testing**: Compara modelos nuevos vs. existentes en producción con subset de usuarios, valida mejoras antes de roll-out completo.

#### Optimización de modelos

Técnicas para hacer modelos más rápidos, usan menos memoria, ejecutable en dispositivos edge.

- **Pruning (Poda)**: Elimina pesos pequeños o neuronas enteras que contribuyen poco. Structural pruning (capas) vs. unstructured pruning (pesos individuales).
- **Destilación de conocimiento (Knowledge distillation)**: Entrena modelo pequeño (student) a imitar modelo grande (teacher). Captura comportamiento complejo en parámetros mucho menores.
- **Low-rank factorization**: Descompone matrices de peso en productos de matrices más pequeñas. LoRA (Low-Rank Adaptation) muy popular para fine-tuning eficiente.
- **Sparse models**: Entrenamientos con sparsidad desde inicio, menos parámetros desde el principio.
- **Neural Architecture Search (NAS)**: Automáticamente encuentra arquitecturas óptimas para dataset/restricciones específicas.

#### Cuantización

Reduce precisión numérica de modelo, disminuyendo tamaño y aumentando velocidad con mínima pérdida de precisión.

- **Post-training quantization (PTQ)**: Cuantiza modelo ya entrenado sin reentrenamiento. Rápido pero potencialmente degradación de performance.
- **Quantization-aware training (QAT)**: Simula cuantización durante entrenamiento, permite al modelo adaptar pesos a precisión reducida. Mejor quality que PTQ.
- **Int8 quantization**: Reduce pesos y activaciones a integers de 8 bits. ~4x reducción de tamaño, generalmente mínima pérdida.
- **Lower-bit quantization**: Int4 o Int2 aún más compresión pero mayor riesgo de degradación.
- **Symmetric vs. asymmetric**: Simétrica centra rango en cero, asimétrica permite offset para mejor utilización del rango.
- **Per-channel vs. per-layer**: Cuantiza parámetros por canal de salida (mejor precision) vs. por capa (más simple).
- **Herramientas**: TensorFlow Lite Quantizer, PyTorch quantization, NVIDIA TensorRT para optimización GPU, ONNX Runtime.

#### Optimización para dispositivos específicos

- **Edge devices**: Móviles, IoT requieren modelos comprimidos. TensorFlow Lite, ONNX Runtime Mobile, Core ML (Apple).
- **GPU acceleration**: NVIDIA CUDA, cuDNN, TensorRT optimiza para hardware NVIDIA. AMD ROCm para AMD GPUs.
- **CPU optimization**: Intel OpenVINO, ONNX Runtime optimiza para CPUs modernas.
