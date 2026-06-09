exports.handler = async (event) => {
  if (event.httpMethod !== 'POST') {
    return { statusCode: 405, body: 'Method Not Allowed' };
  }

  const API_KEY = process.env.GROQ_API_KEY;
  if (!API_KEY) {
    return { statusCode: 500, body: JSON.stringify({ error: 'Clé API Groq manquante' }) };
  }

  try {
    const body = JSON.parse(event.body);

    // Build messages with system prompt included
    const messages = [];
    if (body.system) {
      messages.push({ role: 'system', content: body.system });
    }
    messages.push(...body.messages);

    const response = await fetch('https://api.groq.com/openai/v1/chat/completions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': `Bearer ${API_KEY}`
      },
      body: JSON.stringify({
        model: 'llama-3.3-70b-versatile',
        max_tokens: body.max_tokens || 1000,
        messages: messages,
        temperature: 0.75
      })
    });

    const data = await response.json();

    // Reformat Groq response to match Anthropic format expected by the app
    const text = data.choices?.[0]?.message?.content || 'Je suis momentanément indisponible.';
    const reformatted = {
      content: [{ type: 'text', text }]
    };

    return {
      statusCode: 200,
      headers: {
        'Content-Type': 'application/json',
        'Access-Control-Allow-Origin': '*'
      },
      body: JSON.stringify(reformatted)
    };

  } catch (err) {
    return {
      statusCode: 500,
      body: JSON.stringify({ error: 'Erreur serveur', detail: err.message })
    };
  }
};
