# projeto-banco-de-dados
CREATE DATABASE pizzaria;

USE pizzaria;

CREATE TABLE pizza (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nome VARCHAR(50) NOT NULL,
  descricao VARCHAR(200) NOT NULL
);


CREATE TABLE tamanho (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nome VARCHAR(15) NOT NULL
);

CREATE TABLE preço (
  id INT PRIMARY KEY AUTO_INCREMENT,
  pizza_id INT,
  tamanho_id INT,
  valor DECIMAL(8,2) NOT NULL,
  FOREIGN KEY (pizza_id) REFERENCES pizza(id),
  FOREIGN KEY (tamanho_id) REFERENCES tamanho(id)
);

CREATE TABLE cliente (
  id INT PRIMARY KEY AUTO_INCREMENT,
  nome VARCHAR(60) NOT NULL,
  telefone VARCHAR(20) NOT NULL
);


CREATE TABLE pedido (
  id INT PRIMARY KEY AUTO_INCREMENT,
  cliente_id INT,
  pizza_id INT,
  quantidade INT NOT NULL,
  FOREIGN KEY (cliente_id) REFERENCES cliente(id),
  FOREIGN KEY (pizza_id) REFERENCES pizza(id)
);


CREATE TABLE pizza_pedido (
  id INT PRIMARY KEY AUTO_INCREMENT,
  pizza_id INT,
  pedido_id INT,
  quantidade int not NULL,
  FOREIGN KEY (pizza_id) REFERENCES pizza(id),
  FOREIGN KEY (pedido_id) REFERENCES pedido(id)
);


INSERT INTO pizza (nome, descricao) VALUES
('Margherita', 'Mussarela, tomate, manjericão'),
('Calabresa', 'Calabresa, cebola, mussarela'),
('Frango Catupiry', 'Frango desfiado, catupiry');

INSERT INTO tamanho (nome) VALUES
('Pequena'),
('Média'),
('Grande');


INSERT INTO cliente (nome, telefone) VALUES
('Felipe Cândido', '91234560078'),
('João Pedro', '9876543210'),
('Kahuã Gomes', '9966587571');

INSERT INTO pedido (cliente_id, pizza_id, quantidade) VALUES
(1, 1, 2),
(1, 2, 1),
(2, 3, 3),
(3, 2, 2);


INSERT INTO pizza_pedido (pizza_id, pedido_id, quantidade ) VALUES
(1, 1, 2),
(1, 2, 1),
(2, 3, 3),
(2, 3, 2);

INSERT INTO preço (pizza_id, tamanho_id, valor) VALUES
(1, 1, 25.00),
(1, 2, 35.00),
(1, 3, 45.00),
(2, 1, 27.00),
(2, 2, 37.00),
(2, 3, 47.00),
(3, 1, 30.00),
(3, 2, 40.00),
(3, 3, 50.00);

show tables;
