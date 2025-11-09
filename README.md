library IEEE;
use ieee.std_logic_1164.ALL;
use ieee.std_logic_unsigned.ALL;
use ieee.NUMERIC_std.ALL;

entity ALU_4 IS
	PORT(
		A : in STD_LOGIC_VECTOR(3 downto 0);
		B : in STD_LOGIC_VECTOR(3 downto 0);
		F : in STD_LOGIC_VECTOR(2 downto 0);
		Y : out STD_LOGIC_VECTOR(3 downto 0);
		C_B : out STD_LOGIC);
end ALU_4;

ARCHITECTURE ALU_4_ARCH OF ALU_4 IS

SIGNAL RESULT : STD_LOGIC_VECTOR(4 downto 0) := others(=> '0');
BEGIN
PROCESS(A,B,F)
BEGIN
CASE F IS
	WHEN "000" => RESULT <= '0' & (A AND B);
	WHEN "001" => RESULT <= '0' & (A NAND B);
	WHEN "010" => RESULT <= '0' & (A OR B);
	WHEN "011" => RESULT <= '0' & (A NOR B);
	WHEN "100" => RESULT <= '0' & (A XOR B);
	WHEN "101" => RESULT <= '0' & (A XNOR B);

	WHEN "110" => RESULT <= ('0' & A + '0' & B);
	
	WHEN others 
