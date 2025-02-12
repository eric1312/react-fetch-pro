Cómo Consumir APIs en REACT como un PROFESIONAL

Resumen del Video: Cómo Consumir APIs en REACT como un PROFESIONAL
El video explica cómo consumir APIs en React de manera eficiente y profesional, utilizando buenas prácticas y herramientas modernas. A continuación, se detallan los puntos clave:

1. Introducción a las APIs en React
Las APIs (Interfaces de Programación de Aplicaciones) son esenciales para conectar una aplicación React con servicios externos o backends.

React no tiene una forma nativa de consumir APIs, por lo que se utilizan herramientas como fetch, axios o librerías más avanzadas como React Query o SWR.

2. Uso de fetch para consumir APIs
fetch es la forma nativa de JavaScript para hacer solicitudes HTTP.

Ejemplo básico:
    fetch('https://api.ejemplo.com/datos')
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error('Error:', error));

Limitaciones: fetch no maneja errores de forma automática y requiere más código para gestionar estados de carga y errores.

3. Uso de axios para una mejor gestión de APIs
axios es una librería popular que simplifica las solicitudes HTTP.

Ejemplo:
    axios.get('https://api.ejemplo.com/datos')
      .then(response => console.log(response.data))
      .catch(error => console.error('Error:', error));

Ventajas:
    Manejo automático de errores.
    Interceptores para modificar solicitudes y respuestas.
    Cancelación de solicitudes.

4. Gestión de estados de carga y errores
  Es importante manejar los estados de carga (loading), datos (data) y errores (error) para mejorar la experiencia del usuario.

  Ejemplo con useState y useEffect:
      const [data, setData] = useState(null);
      const [loading, setLoading] = useState(true);
       const [error, setError] = useState(null);
        
        useEffect(() => {
          axios.get('https://api.ejemplo.com/datos')
            .then(response => {
              setData(response.data);
              setLoading(false);
            })
            .catch(error => {
              setError(error);
              setLoading(false);
            });
        }, []);



5. Uso de React Query para gestión avanzada de APIs
React Query es una librería que simplifica la gestión de datos asíncronos en React.

Ventajas:
     Caché automático de datos.
     Revalidación automática de datos.
     Gestión simplificada de estados de carga y errores.

Ejemplo:
    const { data, isLoading, error } = useQuery('datos', () =>
      axios.get('https://api.ejemplo.com/datos').then(res => res.data)
    );


6. Buenas prácticas para consumir APIs
  Separación de preocupaciones: Crear un archivo o carpeta separada para la lógica de las APIs.

Custom Hooks: Crear hooks personalizados para reutilizar la lógica de las APIs.  
  const useFetchData = (url) => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get(url)
      .then(response => {
        setData(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError(error);
        setLoading(false);
      });
  }, [url]);

  return { data, loading, error };
};
Manejo de errores globales: Usar interceptores en axios o React Query para manejar errores de forma global.

. Optimización y rendimiento
Evitar solicitudes innecesarias utilizando caché.

Usar React.memo o useMemo para evitar renders innecesarios.

Cancelar solicitudes pendientes si el componente se desmonta.

8. Herramientas adicionales
SWR: Otra librería popular para la gestión de datos.

Redux Toolkit Query: Para aplicaciones que ya usan Redux.

Conclusión
El video enfatiza la importancia de usar herramientas modernas como React Query o axios para consumir APIs de manera eficiente y profesional. 
Además, destaca la necesidad de seguir buenas prácticas como la separación de preocupaciones, la creación de custom hooks y la optimización del rendimiento.


