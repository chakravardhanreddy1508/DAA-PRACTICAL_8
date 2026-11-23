#include <stdio.h>
int main()
{
    int n, amount, i, j;

    printf("Enter number of coins: ");
    scanf("%d", &n);

    int coin[n];

    printf("Enter coin values: ");
    for(i = 0; i < n; i++)
    {
        scanf("%d", &coin[i]);
    }

    printf("Enter amount: ");
    scanf("%d", &amount);

    int dp[amount + 1];

    dp[0] = 0;

    for(i = 1; i <= amount; i++)
    {
        dp[i] = 99999;
    }

    for(i = 1; i <= amount; i++)
    {
        for(j = 0; j < n; j++)
        {
            if(coin[j] <= i)
            {
                if(dp[i - coin[j]] + 1 < dp[i])
                {
                    dp[i] = dp[i - coin[j]] + 1;
                }
            }
        }
    }

    if(dp[amount] == 100)
        printf("Change is not possible");
    else
        printf("Minimum coins required = %d", dp[amount]);

    return 0;
}
