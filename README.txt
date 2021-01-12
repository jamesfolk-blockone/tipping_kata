--- tipping Project ---

 - How to Build -
   - cd to 'build' directory
   - run the command 'cmake ..'
   - run the command 'make'

 - After build -
   - The built smart contract is under the 'tipping' directory in the 'build' directory
   - You can then do a 'set contract' action with 'cleos' and point in to the './build/tipping' directory
   - ex:
   cleos create account eosio eosio.token EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV



   cleos create account eosio tipping EOS6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV


        cleos set contract tipping ./cmake-build-debug/tipping --abi tipping.abi -p tipping@active
        cleos push action tipping create '[ "alice", "1000000000.0000 SYS"]' -p alice@active


cleos push action tipping create '[ "alice", "1000000000.0000 SYS"]' -p tipping@active
        cleos set contract tipping ./cmake-build-debug/tipping --abi tipping.abi -p tipping@active

 - Additions to CMake should be done to the CMakeLists.txt in the './src' directory and not in the top level CMakeLists.txt



 cleos push action tipping deposit '[ "alice", "100.0000 SYS", "memo" ]' -p alice@active
 cleos push action tipping withdraw '[ "alice", "bob", "25.0000 SYS", "m" ]' -p alice@active

 cleos get currency balance tipping alice SYS
 cleos get currency balance tipping bob SYS






 cleos push action tipping deposit '[ "alice", "100.0000 SYS", "memo" ]' -p alice@active
 cleos get currency balance tipping alice SYS
 cleos push action tipping retire '["100.0000 SYS", "memo"]' -p alice@active
 cleos get currency balance tipping alice SYS

 cleos push action tipping deposit '[ "alice", "100.0000 SYS", "memo" ]' -p alice@active
 cleos get currency balance tipping alice SYS

 cleos get currency balance tipping bob SYS
 cleos push action tipping withdraw '[ "alice", "bob", "25.0000 SYS", "m" ]' -p alice@active
 cleos get currency balance tipping bob SYS

