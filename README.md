import React, { useState } from "react"; // tela de login feita por Gabriela

const WelcomeScreen = () => {
  const [formData, setFormData] = useState({
    name: "",
    phone: "",
    email: "",
    birthDate: "",
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({
      ...formData,
      [name]: value,
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    // Aqui você pode adicionar a lógica para processar os dados do formulário
    console.log(formData);
  };

  return (
    <div style={styles.container}>
      <h1 style={styles.title}>Seja bem-vindo ao Guardher</h1>
      <form onSubmit={handleSubmit} style={styles.form}>
        <div style={styles.formGroup}>
          <label htmlFor="name" style={styles.label}>
            Nome
          </label>
          <input
            type="text"
            id="name"
            name="name"
            value={formData.name}
            onChange={handleChange}
            style={styles.input}
            required
          />
        </div>
        <div style={styles.formGroup}>
          <label htmlFor="phone" style={styles.label}>
            Número de telefone
          </label>
          <input
            type="tel"
            id="phone"
            name="phone"
            value={formData.phone}
            onChange={handleChange}
            style={styles.input}
            required
          />
        </div>
        <div style={styles.formGroup}>
          <label htmlFor="email" style={styles.label}>
            E-mail
          </label>
          <input
            type="email"
            id="email"
            name="email"
            value={formData.email}
            onChange={handleChange}
            style={styles.input}
            required
          />
        </div>
        <div style={styles.formGroup}>
          <label htmlFor="birthDate" style={styles.label}>
            Data de nascimento
          </label>
          <input
            type="date"
            id="birthDate"
            name="birthDate"
            value={formData.birthDate}
            onChange={handleChange}
            style={styles.input}
            required
          />
        </div>
        <button type="submit" style={styles.button}>
          Próximo
        </button>
      </form>
    </div>
  );
};

const styles = {
  container: {
    display: "flex",
    flexDirection: "column",
    alignItems: "center",
    justifyContent: "center",
    height: "100vh",
    backgroundColor: "#f0f0f0",
  },
  title: {
    fontSize: "24px",
    marginBottom: "20px",
  },
  form: {
    display: "flex",
    flexDirection: "column",
    width: "300px",
  },
  formGroup: {
    marginBottom: "15px",
  },
  label: {
    marginBottom: "5px",
    fontSize: "16px",
  },
  input: {
    padding: "10px",
    fontSize: "16px",
    width: "100%",
    boxSizing: "border-box",
  },
  button: {
    padding: "10px",
    fontSize: "16px",
    backgroundColor: "#007bff",
    color: "#fff",
    border: "none",
    cursor: "pointer",
  },
};

export default WelcomeScreen; // fim da tela de login

import React, { useState } from "react"; // tela de pesquisa para a usuária

const SafetyEvaluationScreen = () => {
  const [answers, setAnswers] = useState({
    policePatrol: "",
    hospitalsNearby: "",
    wellLitStreets: "",
    abuseInArea: "",
    safeArea: "",
  });

  const [address, setAddress] = useState("");

  const handleChange = (question, value) => {
    setAnswers({
      ...answers,
      [question]: value,
    });
  };

  const handleAddressChange = (e) => {
    setAddress(e.target.value);
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    // Aqui você pode adicionar a lógica para enviar as respostas e o endereço
    console.log("Endereço:", address);
    console.log("Respostas enviadas:", answers);
  };

  return (
    <div style={styles.container}>
      <h1 style={styles.title}>Informações de Segurança do Endereço</h1>
      <div style={styles.addressContainer}>
        <label htmlFor="address" style={styles.label}>
          Endereço:
        </label>
        <input
          type="text"
          id="address"
          value={address}
          onChange={handleAddressChange}
          style={styles.addressInput}
          placeholder="Digite o endereço"
          required
        />
      </div>
      <form onSubmit={handleSubmit} style={styles.form}>
        <Question
          question="Há policiamento por perto?"
          value={answers.policePatrol}
          onChange={(value) => handleChange("policePatrol", value)}
        />
        <Question
          question="Há hospitais por perto?"
          value={answers.hospitalsNearby}
          onChange={(value) => handleChange("hospitalsNearby", value)}
        />
        <Question
          question="As ruas são bem iluminadas?"
          value={answers.wellLitStreets}
          onChange={(value) => handleChange("wellLitStreets", value)}
        />
        <Question
          question="Já sofreu algum tipo de abuso nessa área?"
          value={answers.abuseInArea}
          onChange={(value) => handleChange("abuseInArea", value)}
        />
        <Question
          question="Você considera esta uma área segura?"
          value={answers.safeArea}
          onChange={(value) => handleChange("safeArea", value)}
        />
        <button type="submit" style={styles.submitButton}>
          Enviar respostas
        </button>
      </form>
    </div>
  );
};

const Question = ({ question, value, onChange }) => {
  return (
    <div style={styles.questionContainer}>
      <p style={styles.questionText}>{question}</p>
      <div style={styles.radioGroup}>
        <label style={styles.radioLabel}>
          <input
            type="radio"
            name={question}
            value="Sim"
            checked={value === "Sim"}
            onChange={() => onChange("Sim")}
          />
          Sim
        </label>
        <label style={styles.radioLabel}>
          <input
            type="radio"
            name={question}
            value="Não"
            checked={value === "Não"}
            onChange={() => onChange("Não")}
          />
          Não
        </label>
      </div>
    </div>
  );
};

const styles = {
  container: {
    display: "flex",
    flexDirection: "column",
    alignItems: "center",
    justifyContent: "center",
    padding: "20px",
    backgroundColor: "#f0f0f0",
    height: "100vh",
  },
  title: {
    fontSize: "24px",
    marginBottom: "10px",
    textAlign: "center",
  },
  addressContainer: {
    marginBottom: "20px",
    width: "100%",
    maxWidth: "400px",
  },
  label: {
    fontSize: "16px",
    marginBottom: "5px",
  },
  addressInput: {
    width: "100%",
    padding: "10px",
    fontSize: "16px",
    borderRadius: "5px",
    border: "1px solid #ccc",
    boxSizing: "border-box",
  },
  form: {
    width: "100%",
    maxWidth: "400px",
  },
  questionContainer: {
    marginBottom: "20px",
  },
  questionText: {
    fontSize: "16px",
    marginBottom: "10px",
  },
  radioGroup: {
    display: "flex",
    gap: "10px",
  },
  radioLabel: {
    display: "flex",
    alignItems: "center",
    gap: "5px",
  },
  submitButton: {
    padding: "10px",
    fontSize: "16px",
    backgroundColor: "#007bff",
    color: "#fff",
    border: "none",
    borderRadius: "5px",
    cursor: "pointer",
    width: "100%",
  },
};

export default SafetyEvaluationScreen; // fim da tela de pesquisa da usuária 

import React from "react"; // tela de ligações

const EmergencyScreen = () => {
  const emergencyContacts = [
    { name: "Delegacia da Mulher ", phone: "+552121340200" },
    { name: "Polícia ", phone: "+5521190" },
    { name: "Bombeiros ", phone: "+5521193" },
    { name: "Ambulância", phone: "+5521192" },
  ];

  const handleCall = (phoneNumber) => {
    window.location.href = `tel:${phoneNumber}`;
  };

  return (
    <div style={styles.container}>
      <h1 style={styles.title}>Emergência </h1>
      <div style={styles.buttonContainer}>
        {emergencyContacts.map((contact, index) => (
          <button
            key={index}
            style={styles.button}
            onClick={() => handleCall(contact.phone)}
          >
            {contact.name}
          </button>
        ))}
      </div>
    </div>
  );
};

const styles = {
  container: {
    display: "flex",
    flexDirection: "column",
    alignItems: "center",
    justifyContent: "center",
    height: "100vh",
    backgroundColor: "#f0f0f0",
    padding: "20px",
  },
  title: {
    fontSize: "24px",
    marginBottom: "20px",
    textAlign: "center",
  },
  buttonContainer: {
    display: "flex",
    flexDirection: "column",
    gap: "10px",
    width: "100%",
    maxWidth: "300px",
  },
  button: {
    padding: "15px",
    fontSize: "16px",
    backgroundColor: "#purple",
    color: "#fff",
    border: "none",
    borderRadius: "5px",
    cursor: "pointer",
    textAlign: "center",
  },
};

export default EmergencyScreen; // fim da tela de ligações 


