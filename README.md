# DSAAssign6

# Q1

```
function findPermutation(s) {
    const n = s.length;
    const perm = [];
    let increase = 0;
    let decrease = n;
    
    for (let i = 0; i < n; i++) {
        if (s[i] === 'I') {
            perm.push(increase);
            increase++;
        } else {
            perm.push(decrease);
            decrease--;
        }
    }
    
    perm.push(increase);
    
    return perm;
}

```

# Q2

```
function searchMatrix(matrix, target) {
    const m = matrix.length;
    const n = matrix[0].length;
    
    let left = 0;
    let right = m * n - 1;
    
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        const row = Math.floor(mid / n);
        const col = mid % n;
        
        if (matrix[row][col] === target) {
            return true;
        } else if (matrix[row][col] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return false;
}

```

# Q3

```
function validMountainArray(arr) {
    const n = arr.length;
    let i = 0;
    
    while (i < n && arr[i] < arr[i + 1]) {
        i++;
    }
    
    if (i === 0 || i === n - 1) {
        return false;
    }
    
    while (i < n && arr[i] > arr[i + 1]) {
        i++;
    }
    
    return i === n - 1;
}

```

# Q4

```
function findMaxLength(nums) {
    const map = new Map();
    map.set(0, -1);
    let maxLen = 0;
    let count = 0;
    
    for (let i = 0; i < nums.length; i++) {
        count += nums[i] === 0 ? -1 : 1;
        
        if (map.has(count)) {
            maxLen = Math.max(maxLen, i - map.get(count));
        } else {
            map.set(count, i);
        }
    }
    
    return maxLen;
}

```

# Q5
```

function minProductSum(nums1, nums2) {
    nums1.sort((a, b) => a - b);
    nums2.sort((a, b) => b - a);
    let sum = 0;
    
    for (let i = 0; i < nums1.length; i++) {
        sum += nums1[i] * nums2[i];
    }
    
    return sum;
}

```

# Q6

```
function findOriginalArray(changed) {
    if (changed.length % 2 !== 0) {
        return [];
    }
    
    changed.sort((a, b) => a - b);
    const original = [];
    const seen = new Set();
    
    for (let num of changed) {
        if (seen.has(num)) {
            seen.delete(num);
        } else {
            original.push(num);
            seen.add(2 * num);
        }
    }
    
    return original;
}

```

# Q7

```

function generateMatrix(n) {
    const matrix = new Array(n).fill(0).map(() => new Array(n).fill(0));
    let top = 0;
    let bottom = n - 1;
    let left = 0;
    let right = n - 1;
    let num = 1;
    
    while (num <= n * n) {
        for (let i = left; i <= right; i++) {
            matrix[top][i] = num;
            num++;
        }
        top++;
        
        for (let i = top; i <= bottom; i++) {
            matrix[i][right] = num;
            num++;
        }
        right--;
        
        for (let i = right; i >= left; i--) {
            matrix[bottom][i] = num;
            num++;
        }
        bottom--;
        
        for (let i = bottom; i >= top; i--) {
            matrix[i][left] = num;
            num++;
        }
        left++;
    }
    
    return matrix;
}

```


# Q8
```

function multiply(mat1, mat2) {
    const m = mat1.length;
    const k = mat1[0].length;
    const n = mat2[0].length;
    const result = new Array(m).fill(0).map(() => new Array(n).fill(0));
    
    for (let i = 0; i < m; i++) {
        for (let j = 0; j < n; j++) {
            for (let x = 0; x < k; x++) {
                result[i][j] += mat1[i][x] * mat2[x][j];
            }
        }
    }
    
    return result;
}

```




