# ============================================
# 🎓 ACTIVIDAD 09 - CONSTRUCTORES Y DESTRUCTORES
# ============================================

# --------------------------------------------
# 📋 DESCRIPCIÓN
# --------------------------------------------
# En esta actividad se explica el ciclo de vida de un objeto
# en C++ y cómo funcionan los constructores y destructores.
# Se agregan a la clase Alumno:
#   🔹 Constructor vacío
#   🔹 Constructor con parámetros
#   🔹 Destructor
#
# El objetivo es VISUALIZAR el ciclo de vida mediante
# mensajes de traza: "Alumno creado" y "Alumno destruido".


# ============================================
# 🔄 1. CICLO DE VIDA DE UN OBJETO
# ============================================
# Todo objeto en C++ pasa por TRES etapas:
#
#   1️⃣ CREACIÓN (construcción):
#      Se reserva memoria y se inicializan los atributos.
#      Aquí interviene el CONSTRUCTOR.
#
#   2️⃣ USO:
#      El objeto existe y sus métodos/atributos pueden
#      ser invocados.
#
#   3️⃣ DESTRUCCIÓN:
#      Cuando el objeto deja de existir (sale de ámbito
#      o se libera la memoria), se llama al DESTRUCTOR.


# ============================================
# 🏗️ 2. CONSTRUCTORES
# ============================================
# DEFINICIÓN:
# Es un método especial que se ejecuta automáticamente
# cuando se crea un objeto.
#
# CARACTERÍSTICAS:
#   ✅ Tiene el mismo nombre que la clase
#   ✅ No tiene tipo de retorno (ni siquiera void)
#   ✅ No se llama explícitamente; el compilador lo invoca
#   ✅ Puede tener múltiples versiones (sobrecarga)


# --------------------------------------------
# A. CONSTRUCTOR VACÍO (por defecto)
# --------------------------------------------
# PROPÓSITO:
# Inicializar los atributos a valores predeterminados.
#
# CARACTERÍSTICAS:
#   🔹 Sin parámetros
#   🔹 Se invoca al declarar un objeto sin argumentos
#   🔹 Si no defines ningún constructor, C++ genera uno
#      por defecto que NO inicializa los atributos
#      (quedan con valores basura)
#   🔹 Por eso conviene definirlo explícitamente
#
# QUÉ HACE:
#   - nombre = ""
#   - edad = 0
#   - promedio = 0.0
#   - Imprime "Alumno creado"


# --------------------------------------------
# B. CONSTRUCTOR CON PARÁMETROS
# --------------------------------------------
# PROPÓSITO:
# Inicializar los atributos con valores específicos
# en el momento de la creación.
#
# CARACTERÍSTICAS:
#   🔹 Se invoca pasando argumentos al declarar el objeto
#   🔹 Permite crear objetos con datos desde el inicio
#
# USO:
#   Alumno a("Ana", 20, 9.5);
#   → Crea un alumno con esos valores
#
# QUÉ HACE:
#   - nombre = n
#   - edad = e
#   - promedio = p
#   - Imprime "Alumno creado"


# --------------------------------------------
# C. LISTA DE INICIALIZACIÓN
# --------------------------------------------
# PROPÓSITO:
# Inicializar atributos ANTES de que el cuerpo del
# constructor se ejecute. Es MÁS EFICIENTE.
#
# SINTAXIS:
# Se coloca después de los dos puntos ":" tras la
# lista de parámetros.
#
# VENTAJA:
#   ✅ Evita una asignación extra
#   ✅ Con la lista, se construye directamente con el
#      valor deseado
#   ✅ Especialmente útil para objetos como string


# ============================================
# 💀 3. DESTRUCTOR
# ============================================
# DEFINICIÓN:
# Es un método especial que se ejecuta automáticamente
# cuando un objeto se destruye.
#
# CARACTERÍSTICAS:
#   🔹 Tiene el mismo nombre que la clase pero precedido
#      por una virgulilla ~
#   🔹 No tiene parámetros ni tipo de retorno
#   🔹 No se puede sobrecargar (solo hay uno por clase)
#   🔹 Se usa para liberar recursos
#
# CUÁNDO SE LLAMA:
#   🔸 Al salir del bloque { } donde se declaró el objeto
#   🔸 Al finalizar el programa (objetos globales/estáticos)
#   🔸 Al eliminar un objeto creado con new usando delete
#   🔸 Para arreglos locales, al salir del ámbito
#
# QUÉ HACE EN ESTA ACTIVIDAD:
#   - Imprime "Alumno destruido"


# ============================================
# 📚 4. ORDEN DE LLAMADAS EN UN ARREGLO
# ============================================
# Al declarar: Alumno alumnos[10];
#
#   🔹 Se llama al CONSTRUCTOR por defecto 10 veces,
#      una por cada objeto del arreglo.
#
#   ⚠️ Si defines un constructor con parámetros y NO
#      defines el vacío, el compilador NO generará el
#      vacío automáticamente, y Alumno alumnos[10];
#      dará ERROR.
#      → Por eso debes definir AMBOS.
#
# Al salir del ámbito (ej: terminar main):
#
#   🔹 Se llama al DESTRUCTOR de cada elemento, en
#      ORDEN INVERSO al de construcción
#      (el último creado se destruye primero).
#
# RESULTADO:
#   → Verás 10 mensajes de "Alumno creado" al inicio
#   → Y 10 de "Alumno destruido" al final.


# ============================================
# 📊 5. RESUMEN DE REGLAS
# ============================================
#
# Aspecto          | Constructor        | Destructor
# -----------------|--------------------|------------------
# Nombre           | Igual que la clase | ~ + nombre clase
# Parámetros       | Puede tener        | Ninguno
# Tipo de retorno  | Ninguno            | Ninguno
# Se llama         | Al crear el objeto | Al destruir
# Sobrecarga       | Sí                 | No
# Puede ser virtual| Sí                 | Sí
# Generado x def.  | Sí (si no hay)     | Sí (si no hay)


# ============================================
# ⚠️ 6. INTERACCIÓN CON LA ACTIVIDAD 8
# ============================================
# REFLEXIÓN IMPORTANTE:
#
# El ejercicio dice "que al crear un alumno aparezca
# 'Alumno creado'".
#
# ⚠️ Si usas un ARREGLO ESTÁTICO, todos los alumnos
#    se crean al INICIO, no al registrarlos.
#
# ✅ Si quieres que aparezca AL REGISTRAR, necesitas
#    crear el objeto en ese momento:
#       - Con new (memoria dinámica)
#       - O con un arreglo dinámico
#
# DECISIÓN:
#   Elige el enfoque según lo que pida tu profesor.


# ============================================
# 💡 7. BUENAS PRÁCTICAS
# ============================================
# ✅ Siempre define el constructor VACÍO si vas a
#    declarar arreglos de objetos.
#
# ✅ Usa la LISTA DE INICIALIZACIÓN para atributos
#    que son objetos (como string), es más eficiente.
#
# ✅ NO pongas lógica compleja en el destructor:
#    debe ser rápido y no lanzar excepciones.
#
# ✅ Libera recursos en el destructor: si usas
#    memoria dinámica (new), libera con delete.
#
# ✅ Documenta el ciclo de vida: los mensajes de
#    traza son útiles para depurar, pero recuerda
#    quitarlos o comentarlos en producción.
#
# ⚠️ CUIDADO: Si creas muchos objetos (ej: 100
#    alumnos), verás muchos mensajes repetidos.
#    → Reduce el tamaño del arreglo (ej: 3) para
#      observar el ciclo sin saturar la consola.


# ============================================
# ❌ 8. ERRORES COMUNES Y SOLUCIONES
# ============================================
#
# Error                              | Solución
# -----------------------------------|------------------
# Olvidar el ~ en el destructor      | Siempre lleva ~
# Poner parámetros al destructor     | No acepta params
# Definir solo constructor con       | Definir también
# parámetros                         | el vacío
# Olvidar el ; al final de la clase  | Cerrar con };
# Llamar explícitamente al           | No se llaman
# constructor/destructor             | manualmente
# Confundir constructor con método   | No tiene tipo
# normal                             | de retorno
# Esperar "Alumno creado" al         | Usar arreglo
# registrar                          | dinámico


# ============================================
# 🎯 9. RESUMEN DE CONCEPTOS CLAVE
# ============================================
# 🔹 Constructor: Método especial que inicializa el
#    objeto al crearlo.
#
# 🔹 Vacío: Sin parámetros, se invoca al declarar
#    sin argumentos.
#
# 🔹 Con parámetros: Permite inicializar con valores
#    específicos.
#
# 🔹 Lista de inicialización: Forma eficiente de
#    inicializar atributos.
#
# 🔹 Destructor: Método especial que se ejecuta al
#    destruir el objeto (~Clase()).
#
# 🔹 Ciclo de vida: Construcción → Uso → Destrucción.
#
# 🔹 Arreglos de objetos: Se construyen todos al
#    declarar el arreglo y se destruyen todos al
#    salir de ámbito.
#
# 🔹 Mensajes de traza: Útiles para visualizar el
#    ciclo de vida, pero pueden saturar la consola
#    con arreglos grandes.


# ============================================
# 🎬 CONCLUSIÓN
# ============================================
# Esta actividad permite VISUALIZAR el ciclo de vida
# de los objetos en C++ mediante mensajes de traza.
#
# Al ejecutar el programa verás:
#   "Alumno creado"   → cuando se crea cada objeto
#   "Alumno destruido" → cuando se destruye cada objeto
#
# Esto ayuda a comprender cuándo y en qué orden se
# ejecutan los constructores y destructores.


# ============================================
# 📄 LICENCIA
# ============================================
# MIT License
