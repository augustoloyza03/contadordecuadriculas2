library ieee;
use ieee.std_logic_1164.all;
use ieee.numeric_std.all;

entity contador_de_cuadriculas is --CONTADOR DE CUANTAS CUADRICULAS CRUZÓ!!!!!!
    port (
        sensor : in std_logic;         -- entrada del sensor desp del antirebote (1 para blanco, 0 para negro)
        clock,rst  : in std_logic;
        a7, a6, a5, a4, a3, a2, a1, a0 : out std_logic
		  );
end contador_de_cuadriculas;

architecture Behavioral of contador_de_cuadriculas is

	 signal count : integer range 0 to 255;
    signal sensor_ant : std_logic;
	 signal count1 : std_logic_vector (7 downto 0);
	 
begin
    process(clock)
    begin
			if rst = '0' then
				count <= 0;
				count1 <= std_logic_vector(To_unsigned(count,8));
				a7 <= count1(7);
				a6 <= count1(6);
				a5 <= count1(5);
				a4 <= count1(4);
				a3 <= count1(3);
				a2 <= count1(2);
				a1 <= count1(1);
				a0 <= count1(0); 
			elsif rising_edge(clock) then --detecta flanco positivo de 0 a 1
            if sensor = '1' and sensor_ant = '0' then
					if count = 255 then
						count <= 0;
					else
						count <= count + 1;
					end if;
					sensor_ant <= sensor;
					
					count1 <= std_logic_vector(To_unsigned(count,8));
					a7 <= count1(7);
					a6 <= count1(6);
					a5 <= count1(5);
					a4 <= count1(4);
					a3 <= count1(3);
					a2 <= count1(2);
					a1 <= count1(1);
					a0 <= count1(0); 
				end if;
			end if;
    end process;
end Behavioral;