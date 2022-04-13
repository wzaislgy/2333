#include<stdio.h>
#include<string.h>
#include<stdlib.h>
int isOperator(char c)
{
    if (c == '+' || c == '-' || c == '*' || c == '/')
        return 1;
    else return 0;
}
void moveOperator(char* p)
{
    while (*p != '\0')
    {
        *p = *(p + 1);
        p++;
    }
}
void moveOperand(float* p, float* end)
{
    while (p != end)
    {
        *p = *(p + 1);
        p++;
    }
}
int main()
{
    char strExp[] = "1-2.5*4+10.2/5.1"; 
    char operators[100] = { '\0' };
    float operands[100];
    float  resualt ;
    //分离运算符
    int operatorsIndex = 0;
    for (int i = 0;i<strlen(strExp);i++)
    {
        if (isOperator(strExp[i]))
        {
            operators[operatorsIndex] = strExp[i];
            operatorsIndex++;
        }
    }
    //分离运算数
    int operandsIndex = 0;
    for (int i = 0; i < strlen(strExp); i++)
    {
        char temp[100] = { '\0'};
        int tempIndex = 0;

        while (!isOperator(strExp[i]))
        {
            temp[tempIndex] = strExp[i];
            i++;
            tempIndex++;
        }
        float floatV =atof(temp);
        operands[operandsIndex++] = floatV;
    }
    for (int i = 0; i < operandsIndex; i++)
    printf("%0.1f\n", operands[i]);
    char* poperator = operators;
    float* poperand = operands;
    while (*poperator != '\0')
    {
        if (*poperator == '*')
        {
            float leftOperand = *poperand;
            float rightOperand = *(poperand + 1);
            float resualt = leftOperand * rightOperand;
            *poperand = resualt;
            moveOperator(poperator);
            moveOperand(poperand + 1, &operands[operandsIndex--]);
        }
        else if (*poperator == '/')
        {
            float leftOperand = *poperand;
            float rightOperand = *(poperand + 1);
            float resualt = leftOperand / rightOperand;
            *poperand = resualt;
            moveOperator(poperator);
            moveOperand(poperand + 1, &operands[operandsIndex--]);
        }
        else
        {
            poperator++;
            poperand++;
        }
    }
    poperator = operators;
    poperand = operands;
    while (*poperator != '\0')
    {
        if (*poperator == '+')
        {
            float leftOperand = *poperand;
            float rightOperand = *(poperand + 1);
            float resualt = leftOperand + rightOperand;
            *poperand = resualt;
            moveOperator(poperator);
            moveOperand(poperand + 1, &operands[operandsIndex--]);
        }
        else if (*poperator == '-')
        {
            float leftOperand = *poperand;
            float rightOperand = *(poperand + 1);
            float resualt = leftOperand - rightOperand;
            *poperand = resualt;
            moveOperator(poperator);
            moveOperand(poperand + 1, &operands[operandsIndex--]);
        }
    }
    printf("resualt=%0.2lf\n", operands[0]);
    return 0;
}
