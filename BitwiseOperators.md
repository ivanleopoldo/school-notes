# Bitwise Operators

The following table lists the Bitwise operators. Assume **A** = 60 and **B** = 13:

<table>
    <tr>
        <th>Operator</th>
        <th>Description</th>
        <th>Example</th>
    </tr>
    <tr>
        <td>
            &amp;
        </td>
        <td>
            Binary AND Operator copies a bit to the result if it exists in both operands. 
        </td>
        <td>
            (A &amp; B) = 12
            <br>
            00111100
            <br>
            <u>00001100</u>
            <br>
            00001100
        </td>
    </tr>
    <tr>
        <td>
            |
        </td>
        <td>
            Binary OR Operator copies a bit if it exists in either operand.
        </td>
        <td>
            (A | B) = 60
            <br>
            00111100
            <br>
            <u>00001100</u>
            <br>
            00111100
        </td>
    </tr>
    <tr>
        <td>
            ^
        </td>
        <td>
            Binary XOR Operator copies the bit if it is set in one operand but not both. 
        </td>
        <td>
            (A ^ B) = 48
            <br>
            00111100
            <br>
            <u>00001100</u>
            <br>
            00110000
        </td>
    </tr>
    <tr>
        <td>
            ~
        </td>
        <td>
            Binary One's Complement Operator is unary and has the effect of 'flipping' bits.
        </td>
        <td>
            (~A) = 195
            <br>
            <u>00111100</u>
            <br>
            11000011
        </td>
    </tr>
    <tr>
        <td>
            &lt;&lt;
        </td>
        <td>
            Binary Left Shift Operator. The left operands value is moved left by the number of bits specified by the right operand.
        </td>
        <td>
            A &lt;&lt; 2
            <br>
            A << 2 = 60 * 2<sup>2</sup> 
            <br>
            A << 2 = 240
        </td>
    </tr>
    <tr>
        <td>
            &gt;&gt;
        </td>
        <td>
            Binary Right Shift Operator. The left operands value is moved right by the number of bits specified by the right operand.
        </td>
        <td>
            A &gt;&gt; 2 = 15
            <br>
            A >> 2 = 60 / 2<sup>2</sup>
        </td>
    </tr>
</table>