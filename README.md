# backgroundgenerator


// Mock DOM elements
const mockColor1 = {
  value: "#ff0000",
  addEventListener: jest.fn()
};

const mockColor2 = {
  value: "#00ff00",
  addEventListener: jest.fn()
};

const mockBody = {
  style: {
    background: "",
  },
};

const mockCss = {
  textContent: "",
};

// Mock querySelector and getElementById functions
document.querySelector = jest.fn((selector) => {
  if (selector === "h3") return mockCss;
  if (selector === ".color1") return mockColor1;
  if (selector === ".color2") return mockColor2;
});

document.getElementById = jest.fn((id) => {
  if (id === "gradient") return mockBody;
});

// Import the function to test
const { setGradient } = require('./your-code-file');

// Unit test using Jest
test('setGradient function should update background and css text content', () => {
  // Arrange
  mockColor1.value = "#ff0000";
  mockColor2.value = "#00ff00";
  
  // Act
  setGradient();

  // Assert
  expect(mockBody.style.background).toBe("linear-gradient(to right, #ff0000, #00ff00)");
  expect(mockCss.textContent).toBe("linear-gradient(to right, #ff0000, #00ff00);");
});
