---
description: "Estándares para componentes frontend en el proyecto"
globs: ["src/components/**/*"]
alwaysApply: false
---
Cuando trabajes en el directorio components:
- Siempre usa Tailwind CSS para estilos
- Usa Framer Motion para todas las animaciones
- Sigue las convenciones de nomenclatura: PascalCase para componentes
- Exporta componentes como named exports
- Incluye PropTypes o TypeScript interfaces en la parte superior
Ejemplo de estructura:
```tsx
interface ButtonProps {
  label: string;
  onClick: () => void;
}
export const Button: React.FC<ButtonProps> = ({ label, onClick }) => {
  return (
    <button className="bg-blue-500 hover:bg-blue-700" onClick={onClick}>
      {label}
    </button>
  );
};