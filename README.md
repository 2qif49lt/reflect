# reflect
c++实现放射的一种方法

```
struct st {
    std::string key;
    int value;
    std::vector<st> children;

    XHB_REFLECT()     
}; 

XHB_REFLECT_STRUCT_BEGIN(st)
XHB_REFLECT_STRUCT_MEMBER(key)
XHB_REFLECT_STRUCT_MEMBER(value)
XHB_REFLECT_STRUCT_MEMBER(children)
XHB_REFLECT_STRUCT_END()

st s{"apple", 3, {{"banana", 7, {}}, {"cherry", 11, {}}}};
auto desc_struct = xhb::type_resolver<st>::get();
cout << desc_struct->dump(&s) << endl;
    
/*  
// dump
st {
    key = std::string{"apple"}
    value = int{3}
    children = std::vector<st>{
        [0]st {
            key = std::string{"banana"}
            value = int{7}
            children = std::vector<st>{}
        }
        [1]st {
            key = std::string{"cherry"}
            value = int{11}
            children = std::vector<st>{}
        }
    }
}
*/
```