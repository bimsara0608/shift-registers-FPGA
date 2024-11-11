library IEEE;
use IEEE.STD_LOGIC_1164.ALL;

entity shift_register is 
    port (
        D : in STD_LOGIC;
        CLK : in STD_LOGIC;
        Q0 : out STD_LOGIC;
        Q1 : out STD_LOGIC;
        Q2 : out STD_LOGIC;
        Q3 : out STD_LOGIC
    );
end shift_register;

architecture Behavioral of shift_register is 
    signal tq0, tq1, tq2, tq3 : STD_LOGIC := '0';
    signal counter : integer := 0;
    signal CLK_divided : STD_LOGIC := '0';
begin 

    
    process(CLK)
    begin  
        if rising_edge(CLK) then
            if counter = 50000000 / 2 then  
                counter <= 0;
                CLK_divided <= not CLK_divided; 
            else
                counter <= counter + 1;	 
            end if;
        end if;
    end process;

    process(CLK_divided)
    begin 
        if rising_edge(CLK_divided) then 
            tq3 <= tq2;
            tq2 <= tq1;
            tq1 <= tq0;
            tq0 <= D;
        end if;
    end process;

    Q0 <= tq0;
    Q1 <= tq1;
    Q2 <= tq2;
    Q3 <= tq3;

end Behavioral;
