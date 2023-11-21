# Configurando-mi-propio-Endpoint-en-mi-Servidor
const axios = require('axios');

app.post('/dar-like', async (req, res) => {
  const { id_foto_instagram } = req.body;

  // Realizar la solicitud a la API de Instagram para dar like
  const response = await axios.post(`https://api.instagram.com/v1/media/${id_foto_instagram}/likes`, {
    access_token: 'TU_ACCESS_TOKEN', // Reemplazar con tu token de acceso de Instagram
  });

  // Verificar la respuesta y enviar la respuesta correspondiente al cliente
  if (response.data.meta.code === 200) {
    res.status(200).json({ mensaje: 'Like exitoso' });
  } else {
    res.status(response.data.meta.code).json({ error: response.data.meta.error_message });
  }
});
